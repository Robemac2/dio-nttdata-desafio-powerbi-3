# Dio-NTTdata Desafio Power BI - 3

### Transformações de dados executadas:

1. Tabela department
    - Removido as colunas de metadados
    - Renomedo colunas e ajuste dos tipos se necessário
        - dname -> Nome_Departamento / Tipo: Texto
        - dnumber -> Código_Departamento / Tipo: Número Inteiro
        - mgr_ssn -> Código_Gerente / Tipo: Número Inteiro
        - mgr_start_date -> Ínicio_Gerente / Tipo: Data
        - dpt_create_date -> Departamento_Criado / Tipo: Data

2. Tabela dependent
    - Removido as colunas de metadados
    - Renomedo colunas e ajuste dos tipos se necessário
        - essn -> Código_Funcionário / Tipo: Número Inteiro
        - dependent_name -> Nome_Dependente / Tipo: Texto
        - sex -> Sexo_Dependente / Tipo: Texto
        - bdate -> Nascimento_Dependente / Tipo: Data
        - relationship -> Relação_Dependente / Tipo: Texto

3. Tabela dept_location
    - Removido as colunas de metadados
    - Renomedo colunas e ajuste dos tipos se necessário
        - dnumber -> Número_Departamento / Tipo: Número Inteiro
        - dlocation -> Localização_Departamento / Tipo: Texto

4. Tabela employee
    - Removido as colunas de metadados
    - Renomedo colunas e ajuste dos tipos se necessário
        - fname -> Nome_Funcionário / Tipo: Texto
        - minit -> Nome_Funcionário_Inicial_Sobrenome / Tipo: Texto
        - lname -> Nome_Funcionário_Sobrenome / Tipo: Texto
            - Colunas mescladas em Nome_Funcionário / Tipo: Texto
        - ssn -> Código_Funcionário / Tipo: Número Inteiro
        - bdate -> Data_Nascimento / Tipo: Data
        - address -> Coluna separada em
            - Logradouro / Tipo: Texto
            - Número_Casa / Tipo: Texto
            - Estado / Tipo: Texto
        - sex -> Sexo_Funcionário / Tipo: Texto
        - salary -> Salário / Tipo: Número Decimal Fixo
        - super_ssn -> Código_Gerente / Tipo: Número Inteiro
            - Valor null é considerado que o funcionário ocupa a posição de gerente e foi atribuido o valor 0 (zero)
        - dno -> Código_Departamento / Tipo: Número Inteiro

5. Tabela Project
    - Removido as colunas de metadados
    - Renomedo colunas e ajuste dos tipos se necessário
        - pname -> Nome_Projeto / Tipo: Texto
        - pnumber -> Número_Projeto / Tipo: Número Inteiro
        - plocation -> Localização_Departamento / Tipo: Texto
        - dnum -> Número_Departamento / Tipo: Número Inteiro

6. Tabela works_on
    - Removido as colunas de metadados
    - Renomedo colunas e ajuste dos tipos se necessário
        - essn -> Código_Funcionário / Tipo: Número Inteiro
        - pno -> Número_Projeto / Tipo: Número Inteiro
        - hours -> Horas_Trabalhadas / Tipo: Número Decimal
    - Removido linha com 0 (zero) horas trabalhadas

7. Tabela employee_-_department
    - Criada à partir da mescla das tabelas employee e department
    - Colunas mantidas
        - Nome_Funcionário
        - Nome_Funcionário_Inicial_Sobrenome
        - Nome_Funcionário_Sobrenome
            - Colunas mescladas em Nome_Funcionário / Tipo: Texto
        - Código_Funcionário
        - Data_Nascimento
        - Logradouro
        - Número_Casa
        - Estado
        - Sexo_Funcionário
        - Salário
        - Código_Gerente
        - Nome_Departamento

8. Tabela manager_employee
    - Criada à partir da mescla das tabelas employee e employee, utilizando o código do gerente da primeira tabela e o código do funcionário da segunda tabela
    - Removido todas as colunas exceto Nome_Funcionário e Nome_Gerente
    - Valor null é considerado que o funcionário ocupa a posição de gerente e foi removido

9. Tabela department_location
    - Criada a partir da mescla das tabelas department e dep_location
    - Colunas mantidas
        - Local_Departamento
        - Código_Departamento
        - Código_Gerente
    - Neste caso foi utilizado a opção mesclar consulta, caso utilize o acrescentar consulta, o resultado após a operação teria colunas com valores nulos