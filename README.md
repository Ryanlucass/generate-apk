
# Autoapk 

#### Guia para gerar apk do seu aplicativo em react-native sem precisar subir a versão na loja de apps. 

Ubuntu e derivados Debian.

1. Crie um arquivo, de preferência no diretório principal 
   ```
	nano autoapk.sh 
   ```

2. Digite o seguinte trecho 

```
#!/bin/bash

echo "Iniciando ..."

cd /home/{user}/{pasta_projeto}

react-native bundle --platform android --dev false --entry-file index.js --bundle-output android/app/src/main/assets/index.android.bundle --assets-dest android/app/src/main/res

cd android 

echo "Copiando arquivo"

cd /home/{user}/{pasta_projeto}/android/app/build/outputs/apk/debug

mv app-debug.apk /home/{user}/{pasta_projeto}/version_apks

mv app-debug.apk Apkgerado_$(date +%Y-%m-%d_%H-%M).apk

echo "O arquivo foi gerado na pasta"
```

3.  Ctrl + O para salvar o arquivo e depois Ctrl + x para sair.

4.  É necessário dar permissão para o arquivo. 
``` chmode +x autoapk.sh```

5. Para rodar o arquivo basta digitar 
`./autoapk.sh`

#### Explicações dos códigos. 

1.  Navega até o diretório raiz do projeto.
2.  Executa o comando `react-native bundle` para criar um pacote de código JavaScript e recursos para o aplicativo.
3.  Navega até o diretório `android`.
4.  Executa o comando `./gradlew assembleDebug` para compilar o aplicativo para depuração.
5.  Move o arquivo `app-debug.apk` para uma pasta de versões prévias de APKs.
6.  Renomeia o arquivo `app-debug.apk` com uma data e hora atual para distinguir das versões anteriores.
7.  Exibe uma mensagem informando que o arquivo APK foi gerado na pasta especificada.

