.data
	range: .asciiz "Enter Positive Integer "
	sum: .asciiz "The Sum is: "
.text
.globl main
.ent main
main:
	li $v0,4
	la $a0,range
	syscall	
	li $v0,5
	syscall
	move $t0,$v0


	
	#counter
        li, $s0, 0
	loop:
        beq $t0, $0, exit
	add $s0, $s0, $t0
	addi $t0, $t0, -1
        j loop

	exit:
	li $v0,4
	la $a0,sum
	syscall	
	li $v0,1
	move $a0,$s0
	syscall	
	li $v0,10
	syscall	
	jr $ra
.end main