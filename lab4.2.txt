
.data
inp1: .asciiz "Enter value in Celsius: "
out1: .asciiz "the value in Fahrenheit: "

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




    

    #calculations
    li $t1, 9
    mult $t0, $t1
    mflo $s0
    mfhi $s1
    add $s0, $s0, $s1
    
    addi $s0, $s0, 2
     

    li $t2, 5
    div $s0, $t2

    


    #result
    mflo $s0
    addi $s0, $s0, 32

    



	
    # print output

    li $v0, 4
    la $a0, out1
    syscall

    li $v0, 1
    move $a0, $s0
    syscall

  

    jr $ra

.end main
