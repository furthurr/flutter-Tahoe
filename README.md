# Guía Completa de Instalación para Entorno Flutter en macOS Silicon  
Basado en el video: https://www.youtube.com/watch?v=-WsFof99CyI

---

## 1. Instalación de Xcode

1. Abrir la terminal y ejecutar:  
```bash
xcode-select --install
```
2. Iniciar sesión con tu cuenta de Apple para poder descargar apps desde App Store.  
3. Instalar **iOS** y la **predicción** dentro de Xcode.  
4. Ejecutar un proyecto simple para comprobar que Xcode funciona correctamente.

---

## 2. Instalar Visual Studio Code (Mac Silicon)

1. Descargar Visual Studio Code.  
2. Instalar la extensión para **Flutter**.  
3. Activar el comando `code` desde VS Code:  
   - Presiona:  
     `Cmd + Shift + P`  
   - Escribe:  
     `Shell Command: Install 'code' command in PATH`

---

## 3. Instalar Flutter

1. Descargar **Flutter para Silicon** desde su página oficial.  
2. Colocar Flutter dentro de la carpeta:

```
/Users/tu_usuario/Developer/
```

> En este documento aparece el nombre: *pedrogomezvasquez*  
> Debes reemplazarlo por tu nombre de usuario real.  
> Si no sabes cuál es, ejecuta:  
> ```bash
> whoami
> ```

3. Configurar el script de la terminal:

```bash
code ~/.zshrc

# Flutter
export PATH="/Users/pedrogomezvasquez/Developer/flutter/bin:$PATH"
```

4. Refrescar el archivo:

```bash
source ~/.zshrc
```

---

## 4. Instalar Homebrew

Ejecutar en terminal:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Agregar Homebrew al script:

```bash
code ~/.zshrc

# Homebrew
eval "$(/opt/homebrew/bin/brew shellenv)"
```

Actualizar zshrc:

```bash
source ~/.zshrc
```

Verificar instalación:

```bash
arch -arm64 brew doctor
```

---

## 5. Instalar Ruby

```bash
brew install ruby
```

Agregar Ruby al PATH:

```bash
export PATH="/opt/homebrew/opt/ruby/bin:$PATH"
```

Actualizar:

```bash
source ~/.zshrc
```

---

## 6. Instalar CocoaPods

Instalar:

```bash
gem install cocoapods
```

Buscar el binario:

```bash
sudo find /opt/homebrew -name pod -type f 2>/dev/null
```

Crear el enlace simbólico:

```bash
sudo ln -s /opt/homebrew/lib/ruby/gems/3.4.0/bin/pod /usr/local/bin/pod
```

Verificar:

```bash
which pod
pod --version
```

Inicializar CocoaPods:

```bash
arch -arm64 pod setup
```

---

## 7. Descargar e instalar Google Chrome
Descargar desde: https://www.google.com/chrome/

---

## 8. Instalar Java

Instalar:

```bash
brew install openjdk@17
```

Agregar al PATH:

```bash
echo 'export PATH="/opt/homebrew/opt/openjdk@17/bin:$PATH"' >> ~/.zshrc
```

Actualizar:

```bash
source ~/.zshrc
```

---

## 9. Instalar Android SDK (Herramientas de línea de comandos)

1. Descargar **Command-line tools** desde la web oficial de Android.  
2. Configurar el script:

```bash
# Android
export ANDROID_HOME="/Users/pedrogomezvasquez/Developer/android"
export PATH=$ANDROID_HOME/cmdline-tools/tools/bin/:$PATH
export PATH=$ANDROID_HOME/emulator/:$PATH
export PATH=$ANDROID_HOME/platform-tools/:$PATH
```

Actualizar:

```bash
source ~/.zshrc
```

Instalar SDK y herramientas:

```bash
sdkmanager --install     "build-tools;35.0.0"     "platforms;android-35"     "cmdline-tools;latest"     "emulator"     "platform-tools"
```

---

## 10. Crear un dispositivo virtual Android (Opcional)

Instalar la imagen:

```bash
sdkmanager --install "system-images;android-35;google_apis_playstore;arm64-v8a"
```

Crear el emulador:

```bash
avdmanager create avd -n pixel_api35 -k "system-images;android-35;google_apis_playstore;arm64-v8a" -d "pixel_7"
```

Ejecutar el emulador:

```bash
emulator -avd pixel_api35
```

---

## 11. Ejecutar Flutter Doctor

```bash
flutter doctor
```

Aceptar licencias de Xcode:

```bash
sudo xcodebuild -license
```

Aceptar licencias de Android:

```bash
flutter doctor --android-licenses
```

---

## 12. Crear tu primer proyecto Hola Mundo

```bash
flutter create hola_mundo
cd hola_mundo
flutter run
```

---

## Documento generado automáticamente para uso personal y técnico.
