# Stored_Procedure

Alter proc sp_Emp
@action varchar(20)=null,
@Id int=0,
@Name varchar(20)=null,
@Email varchar(20)=null,
@Mobile varchar(20)=null,
@Gender varchar(20)=null,
@IsActive bit=null
as 
begin 
if 
@action='select'
begin
select * from Employes where IsActive=1
end 
else if
@action='select_one'
begin
select * from employes where id=@id and IsActive=1
end
else if 
@action='Create'
begin
insert into Employes (Name,Email,Mobile,Gender,IsActive) values (@name,@Email,@mobile,@gender,@IsActive)
end
else if
@action='update'
begin
update employes set Name=@Name where id=@id
end
else if 
@action='Delete'
begin
update employes set IsActive=0 where id=@id 
end
end

sp_Emp 'select'

sp_Emp 'create',0,'Raju Kumar','raju123@gmail',85558545495,'Male',0

sp_Emp 'Delete',2
