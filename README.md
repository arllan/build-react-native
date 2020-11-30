# build-react-native
Diretorio criado com as configurações de build.

# Alterações na aplicação

1.0 -  Neste diretório vai ter o arquivo para alteração do nome do aplicativo:  ***android\app\src\main\res\values\strings.xml***

1.1 - No arquivo vai ter o trecho abaixo. Agora e só alterar o nome.
```
<resources>
	<string  name="app_name">Nome App</string>
</resources>
``` 

3.0 - Neste diretório vai ter as pastas com as imagens nos seus formatos específicos: ***android\app\src\main\res***

3.1 Podemos utilizar o [site](https://romannurik.github.io/AndroidAssetStudio/icons-launcher.html#foreground.type=clipart&foreground.clipart=android&foreground.space.trim=1&foreground.space.pad=0.25&foreColor=rgba(96%2C%20125%2C%20139%2C%200)&backColor=rgb(68%2C%20138%2C%20255)&crop=0&backgroundShape=square&effects=none&name=ic_launcher) para gerar icones genericos nos formatos **Necessários** arredondado e quadrado com os nomes: ***ic_launcher.png e ic_launcher_round.png***

# Testando aplicação

1.0 - Para rodar a aplicação e preciso ***npx react-native start e npx react-native run-android***

# Tutorial e como gerar e configurar chaves de um App

[Site com tutorial](https://medium.com/@legalmenti.thaila/gerando-um-apk-react-native-540ad86f546b)


# Dicas

[Configurando aplicativo em fullscreen](https://medium.com/@ri7nz/react-native-android-window-fullscreen-bf0c7620f479)

[Modificando a orientação da tela para 'landscape' - ultima resposta](https://stackoverflow.com/questions/40235342/react-native-landscape-mode-for-only-one-page)

[Tutorial mostrando como diminuir e criptografar o apk](https://blog.rocketseat.com.br/reduzindo-o-tamanho-das-builds-para-android-no-react-native/)
