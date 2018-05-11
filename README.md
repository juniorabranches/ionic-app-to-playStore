# ionic-app-to-playStore
A step-by-step example to generate your app's .apk for production and publish in the Play Store

# Ambiente WINDOWS

* Esse é um tutorial que eu uso e particularmente nunca tive problemas em publicar meus aplicativos.
* A intenção deste tutorial é exclusivamente ajudar, não é uma regra, mas é a forma que eu faço.
* Levo em consideração que você já tenha o ambiente configurado (JAVA, ANDROID, SDK, JDK...)

# 1) Compilando a aplicação 

* > cordova build android --prod --release

* O .apk gerado encontra-se na pasta do seu projeto > \platforms\android\build\outputs\apk

# 2) Gerando a Keystore 

* A geração da Keystore é única, e feito exclusivamente 1 só vez. Tome cuidado para não perdê-la e grave a senha.

* cd C:\Program Files\Java\VERSAO_DO_JDK\bin
* > keytool -genkey -v -keystore nome-da-keystore.keystore -alias alias_name -keyalg RSA -keysize 2048 -validity 10000

* Responda as perguntas e guarde bem a senha

# 3) Assinando o APK com a Keystore

* Copie o .apk gerado no #1 para a pasta C:\Program Files\Java\VERSAO_DO_JDK\bin

* > cd C:\Program Files\Java\VERSAO_DO_JDK\bin 

* > jarsigner -verbose -sigalg SHA1withRSA -digestalg SHA1 -keystore nome-da-keystore.keystore android-release-unsigned.apk AppViva alias_name

* Informe a senha da keystore e aguarde completar a assinatura

# 4) Gerar o APK de produção

* Copie o .apk assinado no #3 para a pasta C:\Users\USUARIO\AppData\Local\Android\sdk\build-tools\VERSAO_SDK

* > cd C:\Users\USUARIO\AppData\Local\Android\sdk\build-tools\VERSAO_SDK

* > zipalign -v 4 android-release-unsigned.apk NOME_DO_APP.apk

* Aguarde a compilação e..

* Pronto, .apk de produção gerado com sucesso.

# 5) Upar no Google Play Console
