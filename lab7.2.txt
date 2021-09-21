.data
	msg1: .asciiz "Enter the num: "
	out1: .asciiz "The result of factorial is: "

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

	
	#passes the parameters
	move $a0, $t0
	
	jal fact

	#return the function value to the $s0
	move $t0, $v0

	#print message out1
	li $v0, 4
	la $a0, out1
	syscall 

	#printing result
	li $v0, 1
	move $a0, $t0
	syscall
	
	#exit
        li $v0,10
	syscall


fact:
	addi $sp, $sp, -4
	sw $s0, 0($sp)

	#counter
        li, $s0, 1
	loop:
        beq $t0, $0, exit

	
	mult $s0, $t0
	mflo $s0
        mfhi $t1
        add $s0, $s0, $t1


	addi $t0, $t0, -1
        j loop
	
	exit:
	move $v0, $s0
	
	lw $s0, 0($sp)
	addi $sp, $sp, 4

	jr $ra
	
	
	

.end main
	
	