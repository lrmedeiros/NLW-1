algumas bibliotecas não possuem os tipos por default 
separam em outros arquivos

rota:endereço completo da requisição 
recurso: qual entidade estamos acessando do sistema

get: buscar uma ou mais informações do back-end
post: criar uma nova informação no back-end
put: atualizar uma informação existente no back-end
delete: remover uma informação do back-end

post http://localhost:3333/users = criar um usuário
get http://localhost:3333/users = listar usuários
get http://localhost:3333/users/5 = buscar dados do usuário

request param: parametros que vem na propria rota que identificam um recurso
query param: parametros que vem na propria rota
request body: parametro para criação/atualização de informações

 app.get('/users', (request, response) => {
   const search = String(request.query.search);

   const filteredUsers = search ? users.filter(user => user.includes(search)) : users;

   //JSON

   response.json(filteredUsers);
 });

 app.get('/users/:id', (request, response) => {
   const id = Number(request.params.id);

   const user = users[id];

   return response.json(user);
 });

 app.post('/users', (request, response) => {
   const data = request.body;
  
   console.log(data);

   const user = {
     name: data.name,
     email: data.email
   };
   return response.json(user);
 });