
.data
inp: .asciiz "Enter some capital alphabet: "
out: .asciiz "\nThe lower alphabet is: "

.text

.globl main

.ent main

main:

    # print input message 
    li $v0, 4
    la $a0, inp
    syscall

    # get character input
    li $v0, 12
    syscall
    move $t0, $v0

    

    #calculations
    addi $s0, $t0, 32

    



	
    # print output

    li $v0, 4
    la $a0, out
    syscall

    li $v0, 11
    move $a0, $s0
    syscall

  

    jr $ra

.end main
