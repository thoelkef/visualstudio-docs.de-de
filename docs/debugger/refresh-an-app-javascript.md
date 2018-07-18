---
title: Aktualisieren eine uwp-app | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: a45564f34fe0167821febb511a023c01f7c38358
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476279"
---
# <a name="refresh-a-uwp-app-in-visual-studio"></a>Aktualisieren einer uwp-app in Visual Studio
  
 Sie können Änderungen an Code vornehmen, während Sie Debuggen, und aktualisieren Sie eine uwp-app mit JavaScript durch Auswählen der **Windows-app aktualisieren** auf die Schaltfläche der **Debuggen** Symbolleiste. Durch Auswählen dieser Schaltfläche wird die App erneut geladen, ohne den Debugger zu beenden und erneut zu starten. Die Aktualisierungsfunktion ermöglicht es Ihnen, HTML, CSS und JavaScript-Code zu ändern und das Ergebnis schnell anzuzeigen. Diese Funktion wird für uwp-apps unterstützt.  
  
 Aktualisieren hält weder den App-Zustand aufrecht noch reflektiert es die folgenden Änderungen zur App:  
  
-   Paketmanifestdateiänderungen, einschließlich Änderungen an den im Paketmanifest angegebenen Bildern.  
  
-   Verweisänderungen, wie das Hinzufügen oder Entfernen eines SDK-Verweises, oder Änderungen an den Komponenten für Windows-Runtime (.winmd-Dateien).  
  
-   Ressourcenänderungen, wie Änderungen an den Zeichenfolgen in .resjson-Dateien.  
  
-   Projektdateiänderungen, die zu Pfadnamenänderungen, neuen Projektdateien oder gelöschten Dateien führen.  
  
-   Projekt- und Elementeigenschaftenänderungen, wie Änderungen am ausgewählten Debugging-Gerät oder Änderungen an der Paketaktion für eine Datei (im Eigenschaftenfenster).  
  
> [!IMPORTANT]
>  Wenn Sie Verweise oder das Paketmanifest ändern oder andere Änderungen vornehmen, die in der vorangehenden Liste aufgeführt sind, müssen Sie den Debugger beenden und neu starten, um HTML-, CSS- und JavaScript-Quelldateien zu aktualisieren.  
  
### <a name="to-refresh-an-app"></a>So aktualisieren Sie eine App  
  
1.  Wählen Sie mit dem Ihr uwp-Projekt in Visual Studio geöffnet, **lokalen** als Debugziel.
  
     ![Debugzielliste auswählen](../debugger/media/js_select_target.png "JS_Select_Target")  
  
3.  Drücken Sie F5, um die App im Debugmodus auszuführen.  
  
4.  Wechseln Sie zu Visual Studio. 
  
5.  Bearbeiten Sie auf der Homepage Ihrer uwp-App einige der HTML-Datei aus.
  
7.  Klicken Sie auf die **Windows-app aktualisieren** Schaltfläche, die wie folgt: ![aktualisieren Sie Windows-app-Schaltfläche](../debugger/media/js_refresh.png "JS_Refresh"). (Oder drücken Sie F4)  
  
8.  Wechseln Sie zur App. Die app wird erneut geladen, und der aktualisierte HTML-Code wird verwendet, um die app zu rendern.
  
## <a name="see-also"></a>Siehe auch  
 [Schnellstart: Debuggen von HTML und CSS](../debugger/quickstart-debug-html-and-css.md)