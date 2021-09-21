
.data
inp: .asciiz "Enter some positive intger: "
out1: .asciiz "The number is "
out2: .asciiz "prime"
out3: .asciiz "composite"

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
    # print output 1
    li $v0, 4
    la $a0, out1
    syscall
    #check when it is 1
    li, $t4, 1
    beq $t0, $t4, comp
    #calculations
    li $t1, 2
    loop:
    slt $t2, $t1, $t0
    beq $t2, $0, exit

    div $t0, $t1

    mfhi $t3
 
    beq $t3, $0, comp	
    addi $t1,$t1,1
    j loop
    exit:
    li $v0, 4
    la $a0, out2
    syscall
    j end
    comp:
    li $v0, 4
    la $a0, out3
    syscall
    end: 
    jr $ra
 .end main
