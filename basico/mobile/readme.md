# O que é o React Native?

- É a versão do React para desenvolvimento mobile
- Multiplataforma
- Podemos manipular cada plataforma de forma diferente
- Interface Nativa
- O código não é transpilado
- Outra plataformas migrando.

# Arquitetura

Tudo começa com o código Javascript. Ele passa pelo **Metro Bundler/ Packager**
e ele gera o **bundle.js**. Esse **bundle** é repassado para a **bridge** que 
transforma o código para Java e Objective-C.

# Sintaxe

- A declaração dos componentes é igual ao web
- Não utilizamos HTML e sim componentes próprios do React Native
- Aplicamos estilo sem classes ou ID's
- Todo texto é `<Text/>` não existe estilização própria.
- A sintaxe dos estilos é parecida com o css.

# Expo. Vamos usar?

- É uma SKD com um conjunto de funcionalidades prontas para usar no React Native, como câmera, vídeo, integrações com pagamento. 
- Não é necessário configurar um emulador.

Porém não vamos utilizá-lo

- Ele traz limitações sobre o controle do código nativo.
- Várias bibliotecas não tem suporte para o Expo.
- O Expo liberou seu conjunto de ferramentas prontas para serem utilizadas com projetos que não utilizam Expo.


# Criando projeto com react-native-cli

1. No terminal utilizar o comando
   1. `react-native init nome_do_projeto`

# Diferenças para o React.js

1. No React Native os elementos da view não possuem valor semântico.
2. Os elementos no React Native também não possuem estilização própria, toda estilização precisa ser feita pelo desenvolvedor.
3. Todos os components do React Native possuem por padrão `"display: flex"`

Estilos no React Native:

```js
const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#7159c1',
    justifyContent: 'center',
    alignItems: 'center',
  },
  title: {
    fontSize: 40,
    fontWeight: 'bold',
  },
});
```

# Listando projetos da api

- Dependências utilizadas:
  - axios

## Utilizando Axios para desenvolvimento mobile

1. iOS com Emulador
   1. localhost
2. iOS com dispositívo físico
   1. ip da máquina localhost
3. Android com Emulador
   1. adb reverse tcp:3000 tcp:3000 para redirecionar a porta da nossa máquina para a porta do emulador
   2. Realizar processo com emulador aberto, por favor.
4. Android com emulador 2: 
   1. Utilizar IP específico do emulador: 10.0.2.2 (Android Studio)
   2. Utilizar IP específico do emulador: 10.0.3.2 (Genymotion)
5. Android com dispositívo físico
   1. IP da máquina