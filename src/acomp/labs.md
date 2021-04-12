# Laboratório 2

## Exercicio de casa - by RodsCoimbra

::: details Resolução

```asm6502
	.data
a: .word 0
b: .word 0
c: .word 0
d: .word 0
y: .word 0

	.text
rede_neuronal_xor:
	la a1, c
	la a2, d
	la a3, y
	lw s0, a
	lw s1, b
	li s2, 2
	li s3, -2
	jal x1, neuronio
	sw x10, 0(a1)
	li s2, -2
	li s3, 2
	jal x1, neuronio
	sw x10, 0(a2)
	lw s0, 0(a1)
	lw s1, 0(a2)
	li s2, 2
	li s3, 2
	jal x1, neuronio
	sw x10, 0(a3)


	li x17, 1
	ecall
	li x17, 10
	ecall


neuronio:
	addi x2, x2, -12
	sw x1, 8(x2)
	sw s2, 4(x2)
	sw s0, 0(x2)
	jal x1, multiplica
	lw s5, 0(x2)
	addi x2,x2, 4
	sw s3, 4(x2)
	sw s1, 0(x2)
	jal x1, multiplica
	lw s6, 0(x2)
    addi x2, x2, 4
	add s6, s6, s5
	addi s6, s6, -1
	lw x1, 8(x2)
	addi x2, x2, 12
	bge s6, x0, retorno
	li x10, 0
	jalr x0, x1, 0
retorno:
	li x10, 1
	jalr x0, x1, 0

multiplica:
	lw t0, 0(x2)
	lw t1, 4(x2)
	li t2, 0
	bgtz t1, for
	neg t1,t1
	neg t0, t0

for:
	add t2, t0, t2
	addi t1, t1, -1
	bgtz t1, for

	addi x2, x2, -4
	sw t2, 0(x2)
	jalr x0, x1, 0

```

:::



## Lab 2 - by Martim Bento

::: details Resolução
```asm6502
	.data

a:	.word 0
b:	.word 0
c:	.word 1

	.text
#x14 = w1; x15 = w2; x16 = b; x3 =


rede_neuronal_xor:
lw x3, a
lw x4, b
li x14, 2
li x15, -2
li x16, -1
jal neuronio
mv x20, x19
li x14, -2
li x15, 2
li x16, -1
jal neuronio
li x14, 2
li x15, 2
li x16, -1
mv x3, x20
mv x4, x19
jal neuronio  #daqui sai A xor B no x19
mv x20, x19 #gravar A xor B no x20
li x14, 3
li x15, -2
li x16, -2
lw x3, c
lw x4, a
jal neuronio #daqui sai C and (Not A)
mv x21, x19 #gravar C and (Not A) no x21
li x14, 2
li x15, 2
li x16, -1
mv x3, x20
mv x4, x21
jal neuronio #daqui deve sair (A xor B) or (C and (Not A))
jal x0, end

neuronio:
addi sp, sp, -4
sw x1, 0(sp)

mv x10, x3
mv x11, x14
jal multiplica
lw x18, 0(sp)
addi sp, sp, 4
mv x10, x4
mv x11, x15
jal multiplica
lw x19, 0(sp)
addi sp, sp, 4
add x19, x19, x18
add x19, x19, x16
lw x1, 0(sp)
addi sp, sp, 4
blt x19, zero, null
li x19, 1
jalr x0, x1, 0
null:
li x19, 0
jalr x0, x1, 0

multiplica:
li x12, 0 
li x13, 0
blt x11, zero, negative
while:
add x13, x13, x10
addi x12, x12, 1
blt x12, x11, while
addi sp, sp, -4
sw x13, 0(sp)
jalr x0, x1, 0
negative:
sub x13, x13, x10
addi x12, x12, -1
bge x12, x11, negative
addi sp, sp, -4
sw x13, 0(sp)
jalr x0, x1, 0

end:
mv x10, x19
li x17, 1
ecall
li x17, 10
ecall

```
:::