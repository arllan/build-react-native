# build-react-native
Diretorio criado com as configurações de build.


# Criando aplicação

```
npx react-native init "nome do projeto"

OU forma de adicionar versão do react native 

npx react-native init "nome do projeto" --version X.XX.X
```

# Rodando aplicação

```
cd 'pasta do projeto'
npx react-native start
npx react-native run-android
```

#Abrindo Simulador AVD para vistualização do sistema no aparelho - Importante fazer esse passo antes de gerar a versão do .APK

```
1-  Abra o android studio 
2- Com a tela aberta do android studio click em 'Configure'
3- Dentro de 'configure' selecione a opção 'AVD manager'
```

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

# Configurações em uma aplicação

> Local para alterar o nome da aplicação ***android\app\src\main\res\values -strings.xml***

> Site para gerar icone na resolução especificas: [Site 1](https://apetools.webprofusion.com/#/tools/imagegorilla)
[Site 2](https://romannurik.github.io/AndroidAssetStudio/icons-launcher.html#foreground.type=clipart&foreground.clipart=android&foreground.space.trim=1&foreground.space.pad=0.25&foreColor=rgba(96%2C%20125%2C%20139%2C%200)&backColor=rgb(68%2C%20138%2C%20255)&crop=0&backgroundShape=square&effects=none&name=ic_launcher) 

> Local para adicionar icone do aplicativo: ***android\app\src\main\res*** vai ter varias pastas com as resoluções da aplicação

# Testando aplicação

1.0 - Para rodar a aplicação e preciso ***npx react-native start e npx react-native run-android***

# Tutorial e como gerar e configurar chaves de um App

[Site com tutorial](https://medium.com/@legalmenti.thaila/gerando-um-apk-react-native-540ad86f546b)


# Configurações de chave e geração de app.

1- Assista o vídeo do curso do sugeito programador.

2- Faça o procedimento do vídeo para gerar a chave do aplicativo.
3- No arquivo ***\android\gradle.properties*** Faça as seguintes modificações: 

```javascript
MYAPP_RELEASE_STORE_FILE=chaveApp.keystore // informa o nome do arquivo da chave

MYAPP_RELEASE_KEY_ALIAS=chaveApp // informa o alias da chave que colocamos quando foi gerada

MYAPP_RELEASE_STORE_PASSWORD=123456 // chave de criptografia que foi adicionado na hora que geramos

MYAPP_RELEASE_KEY_PASSWORD=123456 // chave de criptografia que foi adicionado na hora que geramos
```  

4- Acesse o arquivo na pasta ***android\app\build.gradle***. Com ele aberto adicione o trecho de código ***bundleInRelease: true*** na função abaixo

```javascript
project.ext.react = [
	enableHermes: false,
	bundleInRelease: true // trecho adicionado a função
]
```
4.1 - adicione o trecho de código logo abaixo de ***defaultConfig***. Dica e procurar o elemento pelo nome.

```javascript
signingConfigs{
	release{
		if(project.hasProperty('MYAPP_RELEASE_STORE_FILE')){
			storeFile file(MYAPP_RELEASE_STORE_FILE)
			storePassword MYAPP_RELEASE_STORE_PASSWORD
			keyAlias MYAPP_RELEASE_KEY_ALIAS
			keyPassword MYAPP_RELEASE_KEY_PASSWORD
		}
	}
}
```

4.2 -  No trecho de código abaixo foi adicionado ***signingConfig signingConfigs.release***

```javascript
buildTypes {

	debug {
	   signingConfig signingConfigs.debug
	}

	release {
	// Caution! In production, you need to generate your own keystore file.
	// see https://reactnative.dev/docs/signed-apk-android.
	signingConfig signingConfigs.debug
	minifyEnabled enableProguardInReleaseBuilds
	proguardFiles getDefaultProguardFile("proguard-android.txt"), "proguard-rules.pro"
	
	signingConfig signingConfigs.release // adicionado
	}

}
```

5- Agora acesse pelo terminal a pasta android e execute o seguinte comando ***gradlew assembleRelease*** e se tudo deu certo ele vai começar a fazer a build do app.

6- O apk foi gerado na seguinte pasta ***android\app\build\outputs\apk\release***

7- Para gerar o app em formato de arquivo bundle execute o seguinte trecho de código ***gradlew bundleRelease***. Lembrando que deve está dentro na pasta ***android*** para executar esse comando. O arquivo do bundle vai estar na seguinte pasta: ***android\app\build\outputs\bundle***



## Aprendendo a atualizar a versão do 'apk' ou '.aab'.

1 - No diretorio ***\android\app\build.gradle*** abra o arquivo e procure pelo seguinte trecho ***versionName e versionCode*** 

2- Atualize ambos por uma versão mais atualizada. Sé caso estiver na versão 1 mude para 2 e assim se segue.

3- Agora e só gerar o app e na playstore como nova versão de um app já existente.



# Dicas

[Configurando aplicativo em fullscreen](https://medium.com/@ri7nz/react-native-android-window-fullscreen-bf0c7620f479)

[Modificando a orientação da tela para 'landscape' - ultima resposta](https://stackoverflow.com/questions/40235342/react-native-landscape-mode-for-only-one-page)

[Tutorial mostrando como diminuir e criptografar o apk](https://blog.rocketseat.com.br/reduzindo-o-tamanho-das-builds-para-android-no-react-native/)

[Lib com ***Modal*** super funcionais](https://jeremybarbet.github.io/react-native-modalize/#/)

[Efeito de load similar ao do facebook](https://www.youtube.com/watch?v=lI9JtRjc2Qo&t=120s)

[Lib de grid nativebase](https://github.com/GeekyAnts/react-native-easy-grid)

[Lib de validação de formulario](https://medium.com/@mauriciosoares_2818/formik-yup-hooks-gerenciando-formul%C3%A1rios-no-react-native-bdfc7018eab9)

[Validação de formulario](https://blog.logrocket.com/react-native-form-validations-with-formik-and-yup/)

[validação com Yup](https://bradhick.medium.com/yup-valida%C3%A7%C3%B5es-no-react-de-uma-forma-muito-simples-700c039114e3)

[Tutorial de como utilizar Styled Components](https://www.youtube.com/watch?v=R3S8DEzEn6s)

[Tutorial de como gerar bundle em vez de apk para loja da playstore](http://www2.decom.ufop.br/terralab/como-publicar-um-aplicativo-feito-em-react-native-na-play-store/#:~:text=Gerando%20o%20AAB%20de%20Lan%C3%A7amento&text=A%20fun%C3%A7%C3%A3o%20bundleRelease%20criar%C3%A1%20um,enviado%20para%20a%20Google%20Play)

[Criando tela de splash screen](https://medium.com/@willjcpower/configurando-a-splash-screen-no-react-native-cli-android-630e4255da22)

[Criando Icone de aplicativo](https://romannurik.github.io/AndroidAssetStudio/icons-launcher.html#foreground.type=clipart&foreground.clipart=android&foreground.space.trim=1&foreground.space.pad=0.25&foreColor=rgba(96%2C%20125%2C%20139%2C%200)&backColor=rgb(68%2C%20138%2C%20255)&crop=0&backgroundShape=square&effects=none&name=ic_launcher)

[Criando formato de arte de tela de splash screen](https://apetools.webprofusion.com/#/tools/imagegorilla)
