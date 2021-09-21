
.data
inp1: .asciiz "Enter first integer: "
inp2: .asciiz "Enter second intger: "
out: .asciiz "Product is:  "

.text

.globl main

.ent main

main:

    # print input message 1
    li $v0, 4
    la $a0, inp1
    syscall

    # get int input
    li $v0, 5
    syscall
    move $t0, $v0


    # print input message 2
    li	$v0, 4
    la $a0, inp2
    syscall

    # get int input
    li $v0, 5
    syscall
    move $t1, $v0




    

    #calculations
    mult $t0, $t1


    #result
    mflo $s0
    mfhi $s1
    add $s0, $s0, $s1

    



	
    # print output

    li $v0, 4
    la $a0, out
    syscall

    li $v0, 1
    move $a0, $s0
    syscall

  

    jr $ra

.end main
