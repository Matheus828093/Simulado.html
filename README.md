<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Simulado de Português</title>

<style>
body{
font-family:Arial;
background:#f4f6ff;
padding:20px;
}

h1{
color:#333;
}

.question{
background:white;
padding:15px;
margin-bottom:15px;
border-radius:10px;
box-shadow:0 2px 5px rgba(0,0,0,0.1);
}

button{
padding:12px 20px;
font-size:16px;
border:none;
border-radius:8px;
background:#4a6cff;
color:white;
cursor:pointer;
}

button:hover{
background:#2f4de0;
}

#result{
margin-top:30px;
background:white;
padding:20px;
border-radius:10px;
}
</style>

</head>

<body>

<h1>📝 Simulado de Português (30 questões)</h1>
<p>Faça o teste e veja sua pontuação. Cada erro terá explicação.</p>

<div id="quiz"></div>

<button onclick="finish()">Finalizar Simulado</button>

<div id="result"></div>

<script>

const questions = [

{
q:"1. Qual tipologia textual conta uma história?",
a:["Descrição","Narração","Injunção","Exposição"],
c:1,
e:"Narração conta uma história com personagens e acontecimentos."
},

{
q:"2. Qual tipologia textual apresenta características de algo?",
a:["Descrição","Narração","Argumentação","Injunção"],
c:0,
e:"Descrição apresenta características de pessoas, lugares ou objetos."
},

{
q:"3. Um texto que tenta convencer o leitor é:",
a:["Narração","Argumentação","Descrição","Exposição"],
c:1,
e:"Argumentação tenta convencer o leitor com opiniões e ideias."
},

{
q:"4. Receita de bolo pertence à tipologia:",
a:["Narração","Descrição","Injunção","Argumentação"],
c:2,
e:"Receitas dão instruções, por isso são textos injuntivos."
},

{
q:"5. Texto que explica um assunto é:",
a:["Exposição","Narração","Descrição","Carta"],
c:0,
e:"Textos expositivos explicam ou informam sobre um tema."
},

{
q:"6. Notícia é exemplo de:",
a:["Tipologia","Gênero textual","Ortografia","Pontuação"],
c:1,
e:"Notícia é um gênero textual usado em jornais."
},

{
q:"7. Carta é um:",
a:["Gênero textual","Tipo de letra","Tempo verbal","Adjetivo"],
c:0,
e:"Carta é um gênero textual usado para comunicação."
},

{
q:"8. A crônica geralmente fala sobre:",
a:["Espaço","Cotidiano","Matemática","Física"],
c:1,
e:"Crônicas normalmente falam sobre situações do dia a dia."
},

{
q:"9. O objetivo da propaganda é:",
a:["Contar história","Convencer","Descrever","Explicar"],
c:1,
e:"Propagandas querem convencer o público."
},

{
q:"10. Tipologia textual significa:",
a:["Tipo de livro","Forma de organizar o texto","Regra gramatical","Tipo de papel"],
c:1,
e:"Tipologia textual é a forma como o texto é organizado."
},

{
q:"11. Manual de instruções é:",
a:["Narração","Injunção","Descrição","Poema"],
c:1,
e:"Manuais ensinam como usar algo."
},

{
q:"12. O título de um texto ajuda a:",
a:["Confundir","Entender o tema","Apagar ideias","Mudar o texto"],
c:1,
e:"O título indica o assunto do texto."
},

{
q:"13. Ideia principal significa:",
a:["Palavra difícil","Mensagem mais importante","Primeira frase","Última frase"],
c:1,
e:"É a mensagem central do texto."
},

{
q:"14. Conto geralmente é:",
a:["Narrativo","Argumentativo","Regra","Explicação"],
c:0,
e:"Contos são histórias narrativas."
},

{
q:"15. Texto que apresenta opinião é:",
a:["Narração","Argumentação","Descrição","Injunção"],
c:1,
e:"Textos argumentativos apresentam opinião."
},

{
q:"16. Receita é exemplo de:",
a:["Gênero textual","Tipologia textual","Ortografia","Pontuação"],
c:0,
e:"Receita é um gênero textual."
},

{
q:"17. Para interpretar um texto devemos:",
a:["Chutar","Ler com atenção","Ignorar título","Ler só uma frase"],
c:1,
e:"É preciso ler com atenção para entender."
},

{
q:"18. Procurar pistas no texto ajuda na:",
a:["Caligrafia","Ortografia","Interpretação","Pontuação"],
c:2,
e:"Pistas ajudam a entender o texto."
},

{
q:"19. Ler o texto duas vezes ajuda a:",
a:["Compreender melhor","Esquecer","Piorar leitura","Apagar ideias"],
c:0,
e:"Ler novamente ajuda a entender melhor."
},

{
q:"20. Gênero textual é:",
a:["Tipo de texto usado na sociedade","Forma do texto","Regra de português","Tipo de letra"],
c:0,
e:"Gênero textual é o tipo de texto usado no dia a dia."
},

{
q:"21. Uma propaganda normalmente quer:",
a:["Ensinar matemática","Convencer pessoas","Contar conto","Explicar ciência"],
c:1,
e:"Propaganda busca convencer o público."
},

{
q:"22. Um texto que descreve um lugar usa principalmente:",
a:["Descrição","Narração","Argumentação","Carta"],
c:0,
e:"Descrição apresenta características."
},

{
q:"23. Jornal e revista costumam publicar:",
a:["Notícias","Receitas","Cartas","Poemas"],
c:0,
e:"Notícia é o principal gênero jornalístico."
},

{
q:"24. Um manual serve para:",
a:["Contar história","Ensinar usar algo","Convencer","Poema"],
c:1,
e:"Manual explica como usar algo."
},

{
q:"25. Texto narrativo geralmente possui:",
a:["Personagens","Equações","Regras","Listas"],
c:0,
e:"Narrativas têm personagens."
},

{
q:"26. Uma receita possui objetivo de:",
a:["Ensinar preparo","Convencer","Narrar","Descrever lugar"],
c:0,
e:"Receita ensina a preparar algo."
},

{
q:"27. Texto argumentativo usa:",
a:["Opiniões","Personagens","Receitas","Equações"],
c:0,
e:"Argumentação apresenta opiniões."
},

{
q:"28. O primeiro passo para interpretar um texto é:",
a:["Ignorar texto","Ler título","Chutar","Fechar"],
c:1,
e:"O título ajuda a entender o tema."
},

{
q:"29. A ideia central do texto é:",
a:["Tema principal","Erro","Pontuação","Letra"],
c:0,
e:"Ideia central é o assunto principal."
},

{
q:"30. Ler com atenção ajuda a:",
a:["Entender texto","Dormir","Apagar","Confundir"],
c:0,
e:"A leitura atenta melhora a compreensão."
}

]

const quiz = document.getElementById("quiz")

questions.forEach((q,i)=>{

let div = document.createElement("div")
div.className="question"

div.innerHTML = "<p>"+q.q+"</p>"

q.a.forEach((opt,j)=>{

div.innerHTML += `
<label>
<input type="radio" name="q${i}" value="${j}">
${opt}
</label><br>
`

})

quiz.appendChild(div)

})

function finish(){

let score = 0
let text = ""

questions.forEach((q,i)=>{

let ans = document.querySelector('input[name="q'+i+'"]:checked')

if(ans){

if(parseInt(ans.value) === q.c){

score++

}else{

text += "<p><b>Questão "+(i+1)+"</b>: "+q.e+"</p>"

}

}else{

text += "<p><b>Questão "+(i+1)+"</b>: "+q.e+"</p>"

}

})

document.getElementById("result").innerHTML =
"<h2>Pontuação: "+score+"/30</h2>"+text

}

</script>

</body>
</html>
