       IDENTIFICATION DIVISION.
       PROGRAM-ID. CALCULADORA.

       ENVIRONMENT DIVISION.

       DATA DIVISION.
       WORKING-STORAGE SECTION.
       01 NUM1          PIC 9(5)V99.
       01 NUM2          PIC 9(5)V99.
       01 RESULT        PIC 9(7)V99.
       01 OPCAO         PIC X.
       01 FIM           PIC X VALUE 'N'.

       PROCEDURE DIVISION.
       MAIN-LOOP.
           PERFORM UNTIL FIM = 'S'
               DISPLAY "=========================="
               DISPLAY "       CALCULADORA        "
               DISPLAY "=========================="
               DISPLAY "Informe o primeiro numero:"
               ACCEPT NUM1
               DISPLAY "Informe o segundo numero:"
               ACCEPT NUM2
               DISPLAY "Escolha a operacao:"
               DISPLAY " + para Adicao"
               DISPLAY " - para Subtracao"
               DISPLAY " * para Multiplicacao"
               DISPLAY " / para Divisao"
               ACCEPT OPCAO

               EVALUATE OPCAO
                   WHEN "+"
                       COMPUTE RESULT = NUM1 + NUM2
                       DISPLAY "Resultado: " RESULT
                   WHEN "-"
                       COMPUTE RESULT = NUM1 - NUM2
                       DISPLAY "Resultado: " RESULT
                   WHEN "*"
                       COMPUTE RESULT = NUM1 * NUM2
                       DISPLAY "Resultado: " RESULT
                   WHEN "/"
                       IF NUM2 = 0
                           DISPLAY "Erro: divisao por zero!"
                       ELSE
                           COMPUTE RESULT = NUM1 / NUM2
                           DISPLAY "Resultado: " RESULT
                       END-IF
                   WHEN OTHER
                       DISPLAY "Operacao invalida!"
               END-EVALUATE

               DISPLAY "Deseja sair? (S/N)"
               ACCEPT FIM
               MOVE FUNCTION UPPER-CASE(FIM) TO FIM
           END-PERFORM.

           DISPLAY "Calculadora encerrada."
           STOP RUN.
