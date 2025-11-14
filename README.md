# 📝 **TaskBoard – Gerenciador de Tarefas Simples**

![Status](https://img.shields.io/badge/status-concluido-brightgreen)
![License](https://img.shields.io/badge/license-MIT-blue)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6-yellow)
![LocalStorage](https://img.shields.io/badge/Storage-LocalStorage-lightgrey)

O **TaskBoard** é um mini gerenciador de tarefas criado com **HTML, CSS e JavaScript**, utilizando **LocalStorage** para salvar tudo automaticamente no navegador.  
É um projeto perfeito para iniciantes que desejam praticar CRUD, organização de código e manipulação do DOM.

---

## 📑 **Índice**

1. [Descrição do Projeto](#-descrição-do-projeto)  
2. [Tecnologias Utilizadas](#-tecnologias-utilizadas)  
3. [Funcionalidades](#-funcionalidades)  
4. [Estrutura do Projeto](#-estrutura-do-projeto)  
5. [Como Executar](#-como-executar)  
6. [Script Completo](#-script-completo)  
7. [Melhorias Futuras](#-melhorias-futuras)  
8. [Licença](#-licença)

---

## 📝 **Descrição do Projeto**

O TaskBoard permite criar, visualizar, editar e excluir tarefas de forma simples.  
Cada ação é salva automaticamente no **LocalStorage**, garantindo que as tarefas permaneçam mesmo após fechar o navegador.

Ideal para aprendizado de:

- CRUD em JavaScript  
- Manipulação do DOM  
- Armazenamento local  
- Organização de código em projetos pequenos  

---

## 🛠 **Tecnologias Utilizadas**

- **HTML5**
- **CSS3**
- **JavaScript ES6**
- **LocalStorage**

---

## ✨ **Funcionalidades**

- ➕ Adicionar tarefas  
- 🖊️ Editar tarefas  
- ❌ Excluir tarefas  
- ✔️ Marcar como concluída  
- 💾 Salvar automaticamente  
- 🎨 Interface simples e responsiva  

---

## 📁 **Estrutura do Projeto**

📂 taskboard
 ├── README.md
 ├── index.html
 ├── style.css
 └── script.js

---

## ▶️ **Como Executar**

1. Baixe ou clone o repositório:

git clone https://github.com/seu-usuario/taskboard.git

2. Abra o arquivo:

index.html

3. Pronto! O projeto roda diretamente no navegador.

---

## 💻 **Código Completo**

### 📌 index.html
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TaskBoard</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

    <h1>TaskBoard</h1>

    <div class="input-area">
        <input type="text" id="taskInput" placeholder="Digite uma tarefa...">
        <button onclick="addTask()">Adicionar</button>
    </div>

    <ul id="taskList"></ul>

    <script src="script.js"></script>
</body>
</html>

body {
    font-family: Arial, sans-serif;
    background: #f2f2f2;
    margin: 0;
    padding: 40px;
    text-align: center;
}

h1 {
    margin-bottom: 20px;
}

.input-area {
    display: flex;
    justify-content: center;
    gap: 10px;
}

input {
    width: 250px;
    padding: 10px;
    border-radius: 8px;
    border: 1px solid #aaa;
}

button {
    padding: 10px 20px;
    border: none;
    background: #4CAF50;
    color: white;
    border-radius: 8px;
    cursor: pointer;
}

button:hover {
    background: #45a049;
}

#taskList {
    margin-top: 30px;
    list-style: none;
    padding: 0;
}

li {
    background: #fff;
    width: 300px;
    margin: 10px auto;
    padding: 12px;
    border-radius: 8px;
    display: flex;
    justify-content: space-between;
    box-shadow: 0 0 4px rgba(0,0,0,0.1);
}

.completed {
    text-decoration: line-through;
    color: gray;
}

li button {
    margin-left: 5px;
    background: #e74c3c;
    border: none;
    padding: 6px 10px;
    color: white;
    border-radius: 6px;
    cursor: pointer;
}

li button:hover {
    background: #c0392b;
}

li button:first-child {
    background: #3498db;
}

li button:first-child:hover {
    background: #2980b9;
}

let tasks = JSON.parse(localStorage.getItem("tasks")) || [];

function save() {
    localStorage.setItem("tasks", JSON.stringify(tasks));
}

function render() {
    const list = document.getElementById("taskList");
    list.innerHTML = "";

    tasks.forEach((task, index) => {
        const li = document.createElement("li");

        li.innerHTML = `
            <span class="${task.done ? "completed" : ""}" onclick="toggle(${index})">
                ${task.text}
            </span>
            <div>
                <button onclick="editTask(${index})">Editar</button>
                <button onclick="deleteTask(${index})">X</button>
            </div>
        `;

        list.appendChild(li);
    });
}

function addTask() {
    const input = document.getElementById("taskInput");

    if (input.value.trim() === "") return;

    tasks.push({ text: input.value, done: false });
    input.value = "";

    save();
    render();
}

function toggle(index) {
    tasks[index].done = !tasks[index].done;
    save();
    render();
}

function deleteTask(index) {
    tasks.splice(index, 1);
    save();
    render();
}

function editTask(index) {
    const newText = prompt("Editar tarefa:", tasks[index].text);

    if (newText !== null && newText.trim() !== "") {
        tasks[index].text = newText;
        save();
        render();
    }
}

render();

🔮 Melhorias Futuras

🌙 Dark Mode

🔄 Filtros (Concluídas / Não concluídas)

🎨 Novo layout com animações

💬 Notificação sonora ao concluir tarefas
