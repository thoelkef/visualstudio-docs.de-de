---
title: Erstellen einer Vue.js-App mithilfe von Node.js
description: Node.js-Anwendungen können in Visual Studio mit dem Vue.js-Framework erstellt werden.
ms.custom: seodec18
ms.date: 07/06/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: a1c9de1c65c5f3f780e6ea4374fa7d96f436f514
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227760"
---
# <a name="create-a-vuejs-application-using-nodejs-tools-for-visual-studio"></a>Erstellen einer Vue.js-Anwendung mit Node.js-Tools für Visual Studio

Visual Studio 2017 bietet eine bessere Unterstützung für das [Vue.js](https://vuejs.org/)-Framework. Dadurch wird die Servicequalität für Entwickler beim Erstellen einer Anwendung mit Vue.js, JavaScript und TypeScript verbessert.

Mit den folgenden Features wird die Entwicklung von Vue.js-Anwendungen in Visual Studio unterstützt:

* Unterstützung für Skript-, Stil- und Vorlagenblöcken in *VUE*-Dateien
* Erkennung des `lang`-Attributs in *VUE*-Dateien
* Vorlagen für Vue.js-Projekte und -Dateien

## <a name="prerequisites"></a>Erforderliche Komponenten

* Sie müssen Visual Studio 2017 Version 15.8 Preview 3 oder höher und die Workload **Node.js-Entwicklung** installiert haben.

    > [!IMPORTANT]
    > Für diesen Artikel sind Features erforderlich, die nur in Visual Studio 2017 Version 15.8 Preview 3 verfügbar sind.

    Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite  [Visual Studio-Downloads](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)  kostenlos herunterladen.

    Falls Sie bereits über Visual Studio verfügen, aber die Workload noch installieren müssen, klicken Sie im linken Bereich des Dialogfelds **Neues Projekt** (**Datei** > **Neu** > **Projekt**) auf den Link **Visual Studio-Installer**. Der Visual Studio-Installer wird gestartet. Klicken Sie auf die Workload **Node.js-Entwicklung** und anschließend auf **Ändern**.

* Zum Erstellen des ASP.NET Core-Projekts müssen die Workloads „ASP.NET und Webentwicklung“ und „Plattformübergreifende .NET Core-Entwicklung“ installiert sein.

* Die Node.js-Laufzeit muss installiert sein.

    Wenn sie nicht bereits installiert ist, installieren Sie die LTS-Version über die [Node.js](https://nodejs.org/en/download/)-Website. Im Allgemeinen erkennt Visual Studio die installierte Node.js-Runtime automatisch. Wenn eine installierte Runtime nicht erkannt wird, können Sie Ihr Projekt so konfigurieren, dass es auf der Eigenschaftenseite auf die installierte Runtime verweist. (Klicken Sie nach dem Erstellen eines Projekts mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Eigenschaften** aus.)

## <a name="create-a-vuejs-project-using-a-template"></a>Erstellen eines Vue.js-Projekts mit einer Vorlage

Ein neues Projekt können Sie mithilfe der neuen Vue.js-Vorlage erstellen. Die Verwendung der Vorlage ist die einfachste Möglichkeit für den Einstieg. Eine ausführliche Anleitung finden Sie unter [Use Visual Studio to create your first Vue.js app (Verwenden von Visual Studio zum Erstellen der ersten Vue.js-App)](../javascript/quickstart-vuejs-with-nodejs.md).

## <a name="create-a-vuejs-project-with-aspnet-core-and-the-vue-cli"></a>Erstellen eines Vue.js-Projekts mit ASP.NET Core und der Vue-Befehlszeilenschnittstelle

Vue.js stellt eine offizielle Befehlszeilenschnittstelle zum schnellen Aufbau eines Gerüst für Projekte bereit. Wenn Sie Ihre Anwendung mit der Befehlszeilenschnittstelle erstellen möchten, verwenden Sie die Anleitung in diesem Artikel zum Einrichten der Entwicklungsumgebung.

> [!IMPORTANT]
> Für diese Anleitung wird vorausgesetzt, dass Sie bereits über Erfahrung mit dem Vue.js-Framework verfügen. Ist dies nicht der Fall, finden Sie unter [Vue.js](https://vuejs.org/) weitere Informationen zum Framework.

### <a name="create-a-new-aspnet-core-project"></a>Erstellen eines neuen ASP.NET Core-Projekts

Für dieses Beispiel wird eine leere ASP.NET Core-Anwendung (C#) verwendet. Sie können jedoch aus einer Vielzahl von Projekten und Programmiersprachen wählen.

#### <a name="create-an-empty-project"></a>Erstellen eines leeren Projekts

1. Öffnen Sie Visual Studio, und wählen Sie im Hauptmenü **Datei** > **Neu** > **Projekt** aus.

1. Wählen Sie unter **Visual C#** > **Web** die Option **ASP.NET Core-Webanwendung** aus, und klicken Sie dann auf **OK**.

    Wenn die Projektvorlage **ASP.NET Core-Webanwendung** nicht vorhanden ist, installieren Sie zunächst die Workload **ASP.NET und Webentwicklung** und die Entwicklungsworkload .**NET Core**. Klicken Sie zum Installieren der Workloads auf den Link **Visual Studio-Installer öffnen** im linken Bereich des Dialogfelds **Neues Projekt** (wählen Sie **Datei** > **Neu** > **Projekt** aus). Der Visual Studio-Installer wird gestartet. Wählen Sie die erforderlichen Workloads aus.

1. Wählen Sie **Leer** aus, und klicken Sie dann auf **OK**.

    Visual Studio erstellt das Projekt, das im Projektmappen-Explorer (rechter Bereich) geöffnet wird.

#### <a name="configure-the-project-startup-file"></a>Konfigurieren der Startdatei des Projekts

* Öffnen Sie die Datei *./Startup.cs*, und fügen Sie der Configure-Methode die folgenden Zeilen hinzu:

    ```csharp
    app.UseDefaultFiles(); // Enables default file mapping on the web root.
    app.UseStaticFiles(); // Marks files on the web root as servable.
    ```

### <a name="install-the-vue-cli"></a>Installieren der Vue-Befehlszeilenschnittstelle

Öffnen Sie zum Installieren des NPM-Moduls vue-cli eine Eingabeaufforderung, und geben Sie `npm install --g vue-cli` oder `npm install -g @vue/cli` für Version 3.0 (derzeit als Betaversion) ein.

### <a name="scaffold-a-new-client-application-using-the-vue-cli"></a>Erstellen eines Gerüsts für eine neue Clientanwendung mit der Vue-Befehlszeilenschnittstelle

1. Wechseln Sie zur Eingabeaufforderung, und geben Sie als aktuelles Verzeichnis das Stammverzeichnis Ihres Projekts ein.

1. Geben Sie `vue init webpack ClientApp` ein, und führen Sie die entsprechenden Schritte aus, wenn Sie aufgefordert werden, weitere Fragen zu beantworten.

#### <a name="modify-the-webpack-configuration-to-output-the-built-files-to-wwwroot"></a>Ändern der Webpack-Konfiguration, sodass die kompilierten Dateien in wwwroot ausgegeben werden

* Öffnen Sie die Datei *./ClientApp/config/index.js*, und ändern Sie `build.index` und `build.assetsRoot` in den wwwroot-Pfad:

    ```js
    // Template for index.html
    index: path.resolve(__dirname, '../../wwwroot/index.html'),

    // Paths
    assetsRoot: path.resolve(__dirname, '../../wwwroot'),
    ```

#### <a name="indicate-the-project-to-build-the-clientapp-each-time-that-a-build-is-triggered"></a>Angeben des Projekts, um die ClientApp bei jedem Auslösen eines Builds zu erstellen

1. Wechseln Sie in Visual Studio zu **Projekt** > **Eigenschaften** > **Buildereignisse**.

1. Geben Sie `npm --prefix ./ClientApp run build` in der **Befehlszeile für Präbuildereignis** ein.

#### <a name="configure-webpacks-output-module-names"></a>Konfigurieren von Namen für Webpack-Ausgabemodule

* Öffnen Sie die Datei *./ClientApp/build/webpack.base.conf.js*, und fügen Sie der Ausgabeeigenschaft folgende Eigenschaften hinzu:

    ```js
    devtoolModuleFilenameTemplate: '[absolute-resource-path]',
    devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
    ```

### <a name="add-typescript-support-with-the-vue-cli"></a>Erweitern der Vue-Befehlszeilenschnittstelle um TypeScript-Unterstützung

Für diese Schritte ist vue-cli 3.0 erforderlich, das derzeit als Betaversion vorliegt.

1. Wechseln Sie zur Eingabeaufforderung, und geben Sie als aktuelles Verzeichnis das Stammverzeichnis des Projekts ein.

1. Geben Sie `vue create ClientApp` ein, und wählen Sie anschließend **Manually select features** (Features manuell auswählen) aus.

1. Wählen Sie zunächst **Typescript** und anschließend weitere gewünschte Optionen aus.

1. Führen Sie die verbleibenden Schritte aus, und beantworten Sie die Fragen.

#### <a name="configure-a-vuejs-project-for-typescript"></a>Konfigurieren eines Vue.js-Projekts für TypeScript

1. Öffnen Sie die Datei *./ClientApp/tsconfig.json*, und fügen Sie `noEmit:true` den Compileroptionen hinzu.

    Durch Festlegen dieser Option verhindern Sie, dass Ihr Projekt mit jedem Kompilieren in Visual Studio überladen wird.

1. Erstellen Sie als Nächstes die Datei *vue.config.js* file in *./ClientApp/*, und fügen Sie folgenden Code hinzu.

    ```js
    module.exports = {
        outputDir: '../wwwroot',

        configureWebpack: {
            output: {
                devtoolModuleFilenameTemplate: '[absolute-resource-path]',
                devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
            }
        }
    };
    ```

    Mit dem vorstehenden Code wird Webpack konfiguriert und der Ordner „wwwroot“ festgelegt.

#### <a name="build-with-vue-cli-30"></a>Kompilieren mit vue-cli 3.0

Die Automatisierung des Buildprozesses wird durch einen unbekannten Fehler bei vue-cli 3.0 verhindert. Jedes Mal, wenn Sie den Ordner „wwwroot“ aktualisieren, müssen Sie für den Ordner „ClientApp“ den Befehl `npm run build` ausführen.

## <a name="limitations"></a>Einschränkungen

* Das Attribut `lang` unterstützt nur die Sprachen JavaScript und TypeScript. Zulässige Werte: js, jsx, ts und tsx.
* Das Attribut `lang` kann nicht mit Template- oder Style-Tags verwendet werden.
* Das Debuggen von Skriptblöcken in *VUE*-Dateien wird aufgrund der Vorverarbeitung nicht unterstützt.
* TypeScript erkennt *VUE*-Dateien nicht als Module. Sie benötigen eine Datei, die Code wie etwa den folgenden enthält, um TypeScript mitzuteilen, wie *VUE*-Dateien aussehen (diese Datei ist in der vue-cli 3.0-Vorlage bereits enthalten).

    ```js
    // ./ClientApp/vue-shims.d.ts
    declare module "*.vue" {
        import Vue from "vue";
        export default Vue;
    }
    ```

* Der Befehl `npm run build` kann bei Verwendung von vue-cli 3.0 nicht als Präbuildereignis für die Projekteigenschaften ausgeführt werden.

## <a name="see-also"></a>Siehe auch

- [Erste Schritte – Leitfaden für Vue](https://vuejs.org/v2/guide).
- [[Vue-CLI-Projekt]](https://github.com/vuejs/vue-cli)
- [Dokumentation zur Konfiguration von Webpack](https://webpack.js.org/configuration/).
