# `Class {}`

**A classe parte do pressuposto um pouco mais comum, e de fácil entendimento até para o usuário, na qual o protótipo da classe principal, usa o `new` e assim é instanciada com vários atributos da mesma classe sendo herdados…**

---
**A classe em JS, usa o objeto de *constructor* para que consiga herdar todos os seus atributos através de parâmetros. Basicamente o objeto principal de *constructor* serve para que consigamos dizer oque deve construída nesse objeto, e não só colocar atributos não mutáveis sem o mesmo...**

**Ainda sim, a partir dessa função principal, ainda conseguimos construir funções, que dentro da classe, são chamadas de métodos!**

```jsx
class User {
    constructor(nome, email, nascimento, role, ativo = true){
/* Atributos definidos nos parãmetros sendo valorizados */
        this.nome = nome;
        this.email = email;
        this.nascimento = nascimento;
        this.role = role || "estudante";
        this.ativo = ativo;
    };
/* Método de exibição de informações sendo instanciado */
    exibirInfos(){
        return `${this.nome}, ${this.email}`;
    };
};
```

Perceba que ainda definimos que o role deve ser definido como padrão de “estudante” já que é o usuário mais comum a todos. Os próximos usuários serão definidos a partir de funções e atributos mais especiais que serão instanciados privativamente a cada um, diferentemente do atributo comum de estudante…

---

### Teste:

```jsx
const novoUser = new User("Joao", "joao@gmail.com", 23/08/2005);
console.log(novoUser);
console.log(novoUser.exibirInfos());
```

### Resultado no console:

```jsx
/* Objeto criado em teste sendo mostrado: */
User {
  nome: 'Joao',
  email: 'joao@gmail.com',
  nascimento: '23/08/2005',
  role: 'estudante',
  ativo: true
}

/* Método de exibição de informações 
sendo chamado para exibir nome e email, 
como informado! */
Joao, joao@gmail.com
```

---

## Super classe:

**Dentro de uma classe, ainda podemos instanciar e buscar atributos de uma outa classe, sendo assim uma árvore de hierarquia e herança, fazendo com que conseguíssemos fazer mais objetos de classes a partir de um filho de uma classe mãe. A partir da função de `super()`;**

**Importamos a classe de User, a classe mãe, para que conseguíssemos a partir de endereçamento o que deve ser chamado para a classe filha. E assim só usamos a função de herda `super()` para que os atributos e métodos sejam herdados!**

```jsx
import User from "./User.js";

class Admin extends User {
    constructor(nome, email, nascimento, role = "admin", ativo = true){
        super(nome, email, nascimento, role, ativo);
    };
};
```

### Teste:

```jsx
const novoAdmin = new Admin("Mly", "mly@gmail.com", "16/01/2005");
console.log(novoAdmin);
console.log(novoAdmin.exibirInfos());
```

### Resultado no console:

```jsx
Admin {
  nome: 'Mly',
  email: 'mly@gmail.com',
  nascimento: '16/01/2005',
  role: 'admin',
  ativo: true
}
Mly, mly@gmail.com
```

---