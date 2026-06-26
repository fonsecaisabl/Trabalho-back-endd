// 1. SEUS DADOS (Exemplo com a opção da Loja)
const produtos = [
    { id: 10, nome: "Teclado", preco: 150 },
    { id: 5, nome: "Mouse", preco: 80 },
    { id: 7, nome: "Monitor", preco: 900 },
    { id: 2, nome: "Fone", preco: 120 },
    { id: 15, nome: "Webcam", preco: 250 }
];

// 2. FUNÇÃO PARA LISTAR
function listarProdutos(lista) {
    console.log("--- Lista de Produtos ---");

    lista.forEach(produto => {
        console.log(`ID: ${produto.id} | Nome: ${produto.nome} | Preço: R$ ${produto.preco}`);
    });
}

// 3. FUNÇÃO DE ORDENAÇÃO (Selection Sort)
function ordenarPorPreco(lista) {
    for (let i = 0; i < lista.length - 1; i++) {
        let menor = i;

        for (let j = i + 1; j < lista.length; j++) {
            if (lista[j].preco < lista[menor].preco) {
                menor = j;
            }
        }

        let temp = lista[i];
        lista[i] = lista[menor];
        lista[menor] = temp;
    }

    return lista;
}

// 4. FUNÇÃO DE BUSCA BINÁRIA
function buscarPorId(lista, idBuscado) {
    let inicio = 0;
    let fim = lista.length - 1;

    lista.sort((a, b) => a.id - b.id);

    while (inicio <= fim) {
        let meio = Math.floor((inicio + fim) / 2);

        if (lista[meio].id === idBuscado) {
            return lista[meio];
        }

        if (lista[meio].id < idBuscado) {
            inicio = meio + 1;
        } else {
            fim = meio - 1;
        }
    }

    return "Produto não encontrado";
}

// --- EXECUÇÃO DOS TESTES ---
listarProdutos(produtos);
const produtosOrdenados = ordenarPorPreco(produtos);
console.log("Produtos Ordenados:", produtosOrdenados);
console.log("Resultado da Busca:", buscarPorId(produtosOrdenados, 5));
