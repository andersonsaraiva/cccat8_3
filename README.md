# Clean Code e Clean Architecture - Turma 8

Aprenda tudo sobre Clean Code, Refactoring, TDD, OO, Ports and Adapters, Clean Architecture, DDD, SOLID e Design Patterns.

> Curso ministrado por [Rodrigo Branas](https://branas.io/)

## Projeto - Parte 2

### Cenário

Vamos implementar um sistema de vendas online com a possibilidade de realizar pedidos com múltiplos itens, cada um deles com uma quantidade variável, calculando o frete, os impostos, aplicando um cupom de desconto e ainda interagindo com o estoque. Além disso teremos ainda fluxos de pagamento e cancelamento do pedido realizado.

### Testes

1. Não deve aplicar cupom de desconto expirado
2. Ao fazer um pedido, a quantidade de um item não pode ser negativa
3. Ao fazer um pedido, o mesmo item não pode ser informado mais de uma vez
4. Nenhuma dimensão do item pode ser negativa
5. O peso do item não pode ser negativo
6. Deve calcular o valor do frete com base nas dimensões (altura, largura e profundidade em cm) e o peso dos produtos (em kg)
7. Deve retornar o preço mínimo de frete caso ele seja superior ao valor calculado

#### Considere

O valor mínimo é de R$10,00
Por enquanto, como não temos uma forma de calcular a distância entre o CEP de origem e destino, será de 1000 km (fixo)
Utilize a fórmula abaixo para calcular o valor do frete

##### Fórmula de Cálculo do Frete

Valor do Frete = distância (km) * volume (m3) * (densidade/100)

##### Exemplos de volume ocupado (cubagem)

- Camera: 20cm x 15 cm x 10 cm = 0,003 m3
- Guitarra: 100cm x 30cm x 10cm = 0,03 m3
- Geladeira: 200cm x 100cm x 50cm = 1 m3

##### Exemplos de densidade

- Camera: 1kg / 0,003 m3 = 333kg/m3
- Guitarra: 3kg / 0,03 m3 = 100kg/m3
- Geladeira: 40kg / 1 m3 = 40kg/m3

##### Exemplos

produto: Camera

- distância: 1000 (fixo)
- volume: 0,003
- densidade: 333
- preço: R$9,90 (1000 * 0,003 * (333/100))
- preço mínimo: R$10,00

produto: Guitarra

- distância: 1000 (fixo)
- volume: 0,03
- densidade: 100
- preço: R$30,00 (1000 * 0,03 * (100/100))

produto: Geladeira

- distância: 1000 (fixo)
- volume: 1
- densidade: 40
- preço: R$400,00 (1000 * 1 * (40/100))

## Projeto - Parte 3

### Testes P3

1. Deve gerar o código do pedido
2. Deve fazer um pedido (caso de uso)
3. Deve simular o frete (caso de uso)
4. Deve validar o cupom de desconto (caso de uso)

#### Considere P3

O código do pedido é formado por AAAAPPPPPPPP onde AAAA representa o ano e o PPPPPPPP representa um sequencial do pedido

#### Importante P3

Implemente os DTOs para cada um dos use cases
Utilize o banco de dados para obter e persistir os dados
