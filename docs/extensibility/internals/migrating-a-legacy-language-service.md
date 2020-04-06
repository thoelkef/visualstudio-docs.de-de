---
title: Migrieren eines Legacy-Sprachdienstes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, migrating
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e2eff3f3a27b7d8a276c8ed776c1e11d5ce332e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707113"
---
# <a name="migrating-a-legacy-language-service"></a>Migrieren eines Legacysprachdiensts
Sie können einen älteren Sprachdienst in eine neuere Version von Visual Studio migrieren, indem Sie das Projekt aktualisieren und dem Projekt eine Datei source.extension.vsixmanifest hinzufügen. Der Sprachdienst selbst funktioniert weiterhin wie bisher, da der Visual Studio-Editor ihn anpasst.

 Ältere Sprachdienste werden als Teil eines VSPackage implementiert, aber die neuere Möglichkeit zum Implementieren von Sprachdienstfunktionen besteht darin, MEF-Erweiterungen zu verwenden. Weitere Informationen zur neuen Möglichkeit zum Implementieren eines Sprachdienstes finden Sie unter [Editor- und Sprachdiensterweiterungen](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Es wird empfohlen, die neue Editor-API so schnell wie möglich zu verwenden. Dadurch wird die Leistung Ihres Sprachdienstes verbessert und Sie können die neuen Editorfunktionen nutzen.

## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>Migrieren einer Visual Studio 2008-Sprachdienstlösung zu einer späteren Version
 Die folgenden Schritte zeigen, wie Sie ein Visual Studio 2008-Beispiel mit dem Namen RegExLanguageService anpassen. Sie finden dieses Beispiel in einer Visual Studio 2008 SDK-Installation im *Visual Studio SDK-Installationspfad*, ordner ,VisualStudioIntegration'Samples'IDE'CSharp'RegExLanguageService''.

> [!IMPORTANT]
> Wenn Ihr Sprachdienst keine Farben definiert, <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> `true` müssen Sie explizit auf das VSPackage festlegen:

```
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]
```

#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>So migrieren Sie einen Visual Studio 2008-Sprachdienst auf eine neuere Version

1. Installieren Sie die neueren Versionen von Visual Studio und des Visual Studio SDK. Weitere Informationen zur Installation des SDK finden Sie unter [Installieren des Visual Studio SDK](../../extensibility/installing-the-visual-studio-sdk.md).

2. Bearbeiten Sie die Datei RegExLangServ.csproj (ohne sie in Visual Studio zu laden).

     Ersetzen `Import` Sie im Knoten, der auf die Datei Microsoft.VsSDK.targets verweist, den Wert durch den folgenden Text.

    ```
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets
    ```

3. Speichern Sie die Datei, und schließen Sie sie.

4. Öffnen Sie die RegExLangServ.sln-Lösung.

5. Das **einwegige Aktualisierungsfenster** wird angezeigt. Klicken Sie auf **OK**.

6. Aktualisieren Sie die Projekteigenschaften. Öffnen Sie das Fenster **Projekteigenschaften,** indem Sie den Projektknoten im **Projektmappen-Explorer**auswählen, mit der rechten Maustaste klicken und **Eigenschaften**auswählen.

    - Ändern Sie auf der Registerkarte **Anwendung** das **Zielframework** auf **4.6.1**.

    - Geben **Debug** Sie **Start external program** ** \<** auf der Registerkarte Debuggen im Feld Externes Programm starten den Installationspfad von Visual Studio>.-

         Geben Sie im Feld **Befehlszeilenargumente** ein /**rootsuffix Exp**.

7. Aktualisieren Sie die folgenden Verweise:

    - Entfernen Sie den Verweis auf Microsoft.VisualStudio.Shell.9.0.dll, und fügen Sie dann Verweise auf Microsoft.VisualStudio.Shell.14.0.dll und Microsoft.VisualStudio.Shell.Immutable.11.0.dll hinzu.

    - Entfernen Sie den Verweis auf Microsoft.VisualStudio.Package.LanguageService.9.0.dll, und fügen Sie dann einen Verweis auf Microsoft.VisualStudio.Package.LanguageService.14.0.dll hinzu.

    - Fügen Sie einen Verweis auf Microsoft.VisualStudio.Shell.Interop.10.0.dll hinzu.

8. Öffnen Sie die VsPkg.cs Datei, `DefaultRegistryRoot` und ändern Sie den Wert des Attributs in

    ```
    "Software\\Microsoft\\VisualStudio\\14.0Exp"
    ```

9. Das ursprüngliche Beispiel registriert seinen Sprachdienst nicht, daher müssen Sie VsPkg.cs das folgende Attribut hinzufügen.

    ```
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]
    ```

10. Sie müssen eine Datei source.extension.vsixmanifest hinzufügen.

    - Kopieren Sie diese Datei aus einer vorhandenen Erweiterung in Ihr Projektverzeichnis. (Eine Möglichkeit, diese Datei zu erhalten, besteht darin, ein VSIX-Projekt zu erstellen (unter **Datei**auf **Neu**klicken , und dann auf **Projekt**klicken. Klicken Sie unter Visual Basic oder C-Taste **Auf Erweiterbarkeit**, und wählen Sie dann **VSIX-Projekt**aus.)

    - Fügen Sie Ihrem Projekt die Datei hinzu.

    - Legen Sie in den **Eigenschaften**der Datei **Buildaktion** auf **Keine**fest.

    - Öffnen Sie die Datei mit dem **VSIX-Manifest-Editor**.

    - Ändern Sie die folgenden Felder:

    - **ID**: RegExLangServ

    - **Produktname**: RegExLangServ

    - **Beschreibung**: Ein Sprachdienst für reguläre Ausdrücke.

    - **Klicken**Sie unter **Neu**auf , wählen Sie den **Typ** in **Microsoft.VisualStudio.VsPackage**aus , legen Sie das **Projekt Quelle** in einem Projekt in der **aktuellen Projektmappe**fest, und legen Sie dann das **Projekt** auf **RegExLangServ**fest.

    - Speichern und schließen Sie die Datei.

11. Erstellen Sie die Projektmappe. Die erstellten Dateien werden in **%USERPROFILE%-AppData-Lokal-Microsoft-VisualStudio-14.0Exp-Erweiterungen,\\MSIT- RegExLangServ**bereitgestellt.

12. Beginnen Sie mit dem Debuggen. Eine zweite Instanz von Visual Studio wurde geöffnet.

## <a name="see-also"></a>Weitere Informationen
- [Erweiterbarkeit von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-extensibility.md)
