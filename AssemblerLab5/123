1.386
.model flat, stdcall
option casemap: none

include C:\masm32\include\windows.inc
include C:\masm32\include\kernel32.inc
includelib C:\masm32\lib\kernel32.lib
include C:\masm32\include\gdi32.inc
includelib C:\masm32\lib\gdi32.lib
include C:\masm32\include\masm32.inc
include C:\masm32\include\user32.inc
includelib C:\masm32\lib\user32.lib
includelib C:\masm32\lib\gdi32.lib
includelib C:\masm32\lib\masm32.lib 

.data

COORD STRUCT
x WORD ?
y WORD ?
COORD ENDS

Message1 db "Input string "
Message2 db "Your string "
ConsoleTitle db 'Assembler Lab 5', 0
xyPos COORD <13, 3>
attributes WORD 0Fh, 0Eh, 0Dh, 0Ch, 0Bh, 0Ah

.code

Main proc

LOCAL InputBufer[128] :BYTE ;буфер дл€ ввода
LOCAL hOutPut :DWORD ;дескриптор дл€ вывода
LOCAL hInput :DWORD ;дескриптор дл€ ввода
LOCAL nRead :DWORD ;прочитано байт
LOCAL nWritten :DWORD ;напечатано байт

;установка заголовка окна
invoke SetConsoleTitle, addr ConsoleTitle

;получение дескриптора дл€ вывода
invoke GetStdHandle, STD_OUTPUT_HANDLE
mov hOutPut, eax

;вывод надписи "Input string "
invoke WriteConsole, hOutPut, addr Message1, 13, addr nWritten, 0

;получение дескриптора дл€ ввода
invoke GetStdHandle, STD_INPUT_HANDLE
mov hInput, eax

;ввод строки
invoke ReadConsole, hInput, addr InputBufer, 10, addr nRead, 0

;вывод надписи "Your string "
invoke WriteConsole, hOutPut, addr Message2, 12, addr nWritten, 0

;вывод введЄнной строки
invoke WriteConsole, hOutPut, addr InputBufer, nRead, addr nWritten, 0

;задержка
;invoke Sleep, 2000d

;установка заголовка окна
invoke SetConsoleTitle, addr ConsoleTitle

;получение дескриптора дл€ вывода
invoke GetStdHandle, STD_OUTPUT_HANDLE
mov hOutPut, eax

;вывод надписи "Input string "
invoke WriteConsole, hOutPut, addr Message1, 13, addr nWritten, 0

;получение дескриптора дл€ ввода
invoke GetStdHandle, STD_INPUT_HANDLE
mov hInput, eax

;ввод строки
invoke ReadConsole, hInput, addr InputBufer, 10, addr nRead, 0

;вывод надписи "Your string "
invoke WriteConsole, hOutPut, addr Message2, 12, addr nWritten, 0

mov edx, [xyPos]
;вывод введЄнной строки
invoke WriteConsoleOutputCharacter, hOutPut, addr InputBufer, nRead, edx, addr nWritten

mov edx, [xyPos]
;задание цвета смежных €чеек на экране
invoke WriteConsoleOutputAttribute, hOutPut, addr attributes, nRead, edx, addr nWritten

;задержка
invoke Sleep, 10000d

;выход
invoke ExitProcess,0
Main endp

end Main
