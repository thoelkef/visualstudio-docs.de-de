---
title: Aktualisieren Sie eine UWP-app | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- JavaScript debugging, refreshing pages [UWP apps]
- debugging, refreshing pages [UWP apps]
- DOM Explorer, Refresh [UWP apps]
- Refresh [UWP apps]
ms.assetid: fd99ee60-fa94-46df-8b17-369f60bfd908
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- uwp
ms.openlocfilehash: 0ee4c97c4ecbf665bbaef39b658a4b96715acb23
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63408642"
---
# <a name="refresh-a-uwp-app-in-visual-studio"></a>Aktualisieren Sie eine UWP-app in Visual Studio

 Sie können Änderungen am Code vornehmen, während Sie debuggen möchten, und Sie dann eine UWP-app mit JavaScript aktualisieren durch Auswählen der **Aktualisieren von Windows-app** Schaltfläche der **Debuggen** Symbolleiste. Durch Auswählen dieser Schaltfläche wird die App erneut geladen, ohne den Debugger zu beenden und erneut zu starten. Die Aktualisierungsfunktion ermöglicht es Ihnen, HTML, CSS und JavaScript-Code zu ändern und das Ergebnis schnell anzuzeigen. Dieses Feature wird für UWP-apps unterstützt.

 Aktualisieren hält weder den App-Zustand aufrecht noch reflektiert es die folgenden Änderungen zur App:

- Paketmanifestdateiänderungen, einschließlich Änderungen an den im Paketmanifest angegebenen Bildern.

- Verweisänderungen, wie das Hinzufügen oder Entfernen eines SDK-Verweises, oder Änderungen an den Komponenten für Windows-Runtime (.winmd-Dateien).

- Ressourcenänderungen, wie Änderungen an den Zeichenfolgen in .resjson-Dateien.

- Projektdateiänderungen, die zu Pfadnamenänderungen, neuen Projektdateien oder gelöschten Dateien führen.

- Projekt- und Elementeigenschaftenänderungen, wie Änderungen am ausgewählten Debugging-Gerät oder Änderungen an der Paketaktion für eine Datei (im Eigenschaftenfenster).

> [!IMPORTANT]
> Wenn Sie Verweise oder das Paketmanifest ändern oder andere Änderungen vornehmen, die in der vorangehenden Liste aufgeführt sind, müssen Sie den Debugger beenden und neu starten, um HTML-, CSS- und JavaScript-Quelldateien zu aktualisieren.

### <a name="to-refresh-an-app"></a>So aktualisieren Sie eine App

1. Wählen Sie Ihr UWP-Projekt in Visual Studio geöffnet, **lokalen Computer** als Debugziel.

     ![Debugzielliste auswählen](../debugger/media/js_select_target.png "JS_Select_Target")

3. Drücken Sie F5, um die App im Debugmodus auszuführen.

4. Wechseln Sie zu Visual Studio.

5. Bearbeiten Sie auf der Startseite Ihrer UWP-App Teil der HTML-Code aus.

7. Klicken Sie auf die **Aktualisieren von Windows-app** Schaltfläche an, welche sieht wie folgt aus: ![Windows-app-Schaltfläche "Aktualisieren"](../debugger/media/js_refresh.png "JS_Refresh"). (Oder drücken Sie F4)

8. Wechseln Sie zur App. Die app wird erneut geladen, und das aktualisierte HTML zum Rendern der app verwendet wird.

## <a name="see-also"></a>Siehe auch
- [Schnellstart: Debug HTML and CSS (Schnellstart: Debuggen von HTML und CSS)](../debugger/quickstart-debug-html-and-css.md)