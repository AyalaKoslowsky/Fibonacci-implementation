.data

inMsg: .asciiz "Enter a number: "
msg: .asciiz "Calculating F(n) for n = "
fibNum: .asciiz "\nF(n) is: "
.text

main:

	li $v0, 4
	la $a0, inMsg
	syscall

	# take input from user
	li $v0, 5
	syscall
	addi $a0, $v0, 0
	
	jal print_and_run
	
	# exit
	li $v0, 10
	syscall

print_and_run:
	addi $sp, $sp, -4
	sw $ra, ($sp)
	
	add $t0, $a0, $0 

	# print message
	li $v0, 4
	la $a0, msg
	syscall

	# take input and print to screen
	add $a0, $t0, $0
	li $v0, 1
	syscall

	jal fib

	addi $a1, $v0, 0
	li $v0, 4
	la $a0, fibNum
	syscall

	li $v0, 1
	addi $a0, $a1, 0
	syscall
	
	lw $ra, ($sp)
	addi $sp, $sp, 4
	jr $ra

fib: 
	beq $a0, $zero, zero
	beq $a0, 1, one

	add $t0, $a0, $zero
	add $s1, $zero, $zero
	addi $s2, $zero, 1
	bne $t0, $zero, fib_rec

zero:
	add $v0, $zero, $zero
	j return

one:
	addi $v0, $zero, 1
	j return

fib_rec:
	subi $t0, $t0, 1
	add $s3, $s1, $s2
	add $s1, $s2, $zero
	add $s2, $s3, $zero
	bne $t0, $zero, fib_rec
	add $v0, $s1, $zero

return:
	jr $ra
