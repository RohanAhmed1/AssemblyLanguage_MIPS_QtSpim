.data
	msg1: .asciiz "Enter the num: "
	msg2: .asciiz "Enter the pow: "
	out1: .asciiz "The result of num^pow is: "

.text
.globl main
.ent main

main:
	#print Enter the num
	li $v0, 4
	la $a0, msg1
	syscall
	
	#input the num
	li $v0, 5
	syscall
	
	#$t0 <- num
	move $t0, $v0

	#print Enter the pow
	li $v0, 4
	la $a0, msg2
	syscall

	#input the pow
	li $v0, 5
	syscall

	#$t1 <- pow
	move $t1, $v0
	
	#passes the parameters
	move $a0, $t0
	move $a1, $t1
	
	jal numpow

	#return the function value to the $t2
	move $t2, $v0

	#print message out1
	li $v0, 4
	la $a0, out1
	syscall 

	#printing result
	li $v0, 1
	move $a0, $t2
	syscall
	#exit
        li $v0,10
	syscall


numpow:
	addi $sp, $sp, -4
	sw $s0, 0($sp)

	
	li $s0, 2

	li $t0, 1

	loop:
	slt $t1, $t0, $a1
	beq $t1, $0, exit
	mult $s0, $a0
	mflo $t2
	mfhi $t1
	add $s0, $t1, $t2
	addi $t0,$t0,1
	j loop

	exit:
	move $v0, $s0
	
	lw $s0, 0($sp)
	addi $sp, $sp, 4
	jr $ra

.end main
	
	