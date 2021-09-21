
.data
inp: .asciiz "Enter some integer: "
out: .asciiz "The 2's complement is: "

.text

.globl main

.ent main

main:

    # print input message 
    li $v0, 4
    la $a0, inp
    syscall

    # get int input
    li $v0, 5
    syscall
    move $t0, $v0

    

    #calculations
    
    nor $t0, $t0, $t0
    addi $s0, $t0, 1

    



	
    # print output

    li $v0, 4
    la $a0, out
    syscall

    li $v0, 1
    move $a0, $s0
    syscall

  

    jr $ra

.end main
