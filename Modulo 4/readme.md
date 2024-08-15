###	Criação de uma instância na Azure para MySQL
 ![image](https://github.com/user-attachments/assets/64f63f97-fabe-40d2-aa34-45463a2c511d)

###	Criar o Banco de dados com base disponível no github
 ![image](https://github.com/user-attachments/assets/681f7ef5-969f-443b-be73-3e03a8ee257e)

###	Integração do Power BI com MySQL no Azure 
 ![image](https://github.com/user-attachments/assets/cbdf12b0-e34c-474f-98e5-a86f7ac76b5a)

###	Verificar problemas na base a fim de realizar a transformação dos dados
    Problema ao inserir, sendo assim eliminado, inserir os dados e adicionar novamente.
    ALTER TABLE `azure_company`.`employee` 
    DROP FOREIGN KEY `fk_employee`;
    ALTER TABLE `azure_company`.`employee` 
    DROP INDEX `fk_employee` ;

    alter table employee 
    	add constraint fk_employee 
    	foreign key(Super_ssn) references employee(Ssn)
        on delete set null
        on update cascade;

## No Power BI
#### Removocao de colunas "Table"  em todas as tabelas
#### Modificao de todas numeros para inteiro
#### Valores monetários(salary) para o tipo double preciso
#### Employese.super_ssn gerente Fname "james"
#### Coluna Address divido por delimitador '-' em em StreetCod, Street, City, State
![image](https://github.com/user-attachments/assets/066b311a-d2e2-4e2c-a782-1389586cfaf4)

#### Mescle as colunas de Nome e Sobrenome para ter apenas uma coluna definindo os nomes dos colaboradores [Fname] & " " & [Lname]

#### Employee e departament
![image](https://github.com/user-attachments/assets/d9041a18-9091-41ac-913a-f4396395f52a)

### colaboradores e respectivos nomes dos gerentes 
    Select concat(c.fname, " ", c.lname), 
    (select concat(g.fname, " ", g.lname) from employee g where g.ssn = c.Super_ssn)  gerente
    from employee c;

### Mesclar e não o atribuir
#### Nesse exemplo queriamos mostrar os colocaboradores por departamento, sendo assim melhor e ter uma coluna a esquerda ou direita para melhor analise do que ter uma linha acrescentado que nao ajudaria na intepretacao dos resultados. E mesma leitura para a outra figura.

