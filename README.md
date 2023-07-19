# Warker

Olá! Muito obrigado por participar da avalição técnica para integrar a equipe de desenvolvimento da W16.

Criamos esta avaliação para avaliar seu conhecimento em lógica de programação, capacidade de investigar e conhecer novas ferramentas, organização e qualidade de código e especialmente, sua criatividade.

No mundo pós-apocaliptico de 2023, o combustível tem um valor inestimável. Gangues bárbaras lutam até a morte pelo controle desse valioso recurso e a W16 está desenvolvendo o aplicativo **WARKER**, que é a última esperança da humanidade em trazer um pouco de paz e ordem à esse mundo devastado. Esse aplicativo deve consumir uma API REST que indica os postos de gasolina das diversas cidades, sua localização e o nível dos seus reservatórios. Lembre-se de que não há mais lei e a sua vida depende do sucesso dessa aplicação. Marcopoc não fica feliz quando o seu carro falhar devido a falta de gasolina e você NÃO quer deixar o Marcopoc irritado...

## Material

Todos os dados necessários serão entregues por um backend feito pela W16. Os endpoints são apenas de consulta, não havendo a necessidade de criação de conteúdo nem autenticação 🤩.

## Endpoints

URL BASE: `https://warker-api.vercel.app/api`

### Modelos

```ts
type Coordinates: {
    latitude: number;
    longitude: number;
}

type City = {
    id: number;
    name: string;
    coords: Coordinates
}

type GasStation = {
    id: number;
    repository: number;
    coords: Coordinates
}
```

### Cidades

#### `[GET] /cities`

Retorno de todas as cidades de forma paginada

```ts
// Request - query parameters
type per_page?: number
type page?: number
type search?: string
```

```ts
// Response
type Response = {
    data: City[]
    meta: {
        page: number;
        total: number;
        per_page: number;
        total_pages: number;
    }
}
```

#### `[GET] /cities/nearby?latitude=<lat>&longitude=<lng>`

Retorna a capital mais proxima ao usuário

```ts
// Request - query parameters
type latitude: number
type longitude: number
```

```ts
// Response

// 200
type SuccessfulResponse = City


// 404
type ErrorResponse = {
    message: string
}
```

### Postos de Gasolina

#### `[GET] /cities/<city_id>/gas_stations`

Retorno paginado de todos os postos presentes na cidade.

```ts
// Request - query parameters
type per_page?: number
type page?: number
```

```ts
// Response
type Response = {
    data: GasStation[]
    meta: {
        page: number;
        total: number;
        per_page: number;
        total_pages: number;
    }
}
```

## O que é esperado

Esperamos que você consiga fazer a **estimativa aproximada** do tempo de trabalho necessário para a entrega das funcionalidades, que serão descritas na próxima seção.

Como parte do desafio também é desejado que você consiga escolher e explicar os motivos por qual as ferramentas e tecnologias foram usadas e aplicadas.

### O que deve ser construído

Uma aplicação simples de uma a duas páginas, onde o usuário deve entrar na aplicação e conseguir visualizar os postos de gasolina mais próximos a sua localização e ter acesso ao nível de seu repositório. **OBS:** Devido como o backend foi construído sabemos que os postos mais proximos irão ser da capital mais próxima ao usuário.

Ao menos uma tela deve utilizar alguma solução para a apresentação do map e os marcadores dos postos de gasolina.

#### Bônus

- Splashscreen
  
- Navegação
  
- Filtro por cidades na tela do mapa
  

#### Sobre a entrega

- Acesso ao repositório GIT
  
- APK funcional, podendo ser usado sem o metro. (App de produção)
