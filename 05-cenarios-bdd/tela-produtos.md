# 🧪 Cenários de Testes – Tela de Produtos

## Funcionalidade: Acesso aos Produtos
Eu como usuário da Loja  
Quero acessar a página de produtos  
Para visualizar todos os produtos  
E poder acessar o detalhe de cada um

## Cenário: Acessar o detalhe do produto
```gherkin
Funcionalidade: Acesso aos produtos
  Cenário: Acessar o detalhe do produto
    Dado que o usuário esteja na página de produtos
    Quando acessar um dos CARDs de produto
    Então deve visualizar a página de detalhe selecionado
```
