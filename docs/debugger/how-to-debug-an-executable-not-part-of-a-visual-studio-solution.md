---
title: 'Gewusst wie: Debuggen einer app, die nicht Teil von Visual Studio-Projektmappe | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/19/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 993af0d15245ef6391f2c9c4eb0e755e24920fe3
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388581"
---
# <a name="debug-an-app-that-isnt-part-of-a-visual-studio-solution-c-c-visual-basic-f"></a>Debuggen einer app, die nicht Teil von Visual Studio-Projektmappe (C++, C#, Visual Basic F#)

Sie möchten eine app zu debuggen (*.exe* Datei), die nicht Teil von Visual Studio-Projektmappe. Sie oder eine andere Person möglicherweise erstellt die app außerhalb von Visual Studio, oder Sie haben die app von einer anderen Stelle. 

Die übliche Vorgehensweise zum Debuggen einer app, die in Visual Studio nicht vorhanden ist, starten Sie die app außerhalb von Visual Studio, und fügen Sie über **an den Prozess anhängen** in Visual Studio-Debugger. Weitere Informationen finden Sie unter [Anfügen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
Anfügen an eine app erfordert manuelle Schritte, die einige Sekunden dauern. Aufgrund dieser Verzögerung Anfügen nicht die Lösung ein Problems beim Start zu debuggen, oder eine app, die für Benutzer nicht warten, Eingabe- und schnell abgeschlossen. 

In diesen Fällen können Sie ein Visual Studio-EXE-Projekt für die app zu erstellen oder importieren Sie es in einer vorhandenen C#, Visual Basic oder C++ Lösung. EXE-Projekte werden nicht von allen Programmiersprachen unterstützt. 

>[!IMPORTANT]
>Features für eine app, die in Visual Studio erstellt wurde nicht für das Debuggen sind eingeschränkt, und, ob Sie für die app anfügen, oder fügen Sie es Visual Studio-Projektmappe hinzu. 
>
>Wenn Sie den Quellcode haben, ist der beste Ansatz, den Code in Visual Studio-Projekt zu importieren. Führen Sie dann einen Debugbuild der app ein.
>
>Wenn Sie nicht über den Quellcode verfügen, und die app keine [Debuginformationen](../debugger/how-to-set-debug-and-release-configurations.md) in einem kompatiblen Format zur Verfügung Debugfunktionen sind nur sehr wenige. 

### <a name="to-create-a-new-exe-project-for-an-existing-app"></a>Um eine neue EXE-Projekt für eine vorhandene app zu erstellen.  
   
1. Wählen Sie in Visual Studio **Datei** > **öffnen** > **Projekt**.  
   
1. In der **geöffneten Projekt** wählen Sie im Dialogfeld **alle Projektdateien**, sofern nicht bereits in der Dropdownliste neben ausgewählt, **Dateiname**.  
   
1. Navigieren Sie zu der *.exe* , wählen Sie ihn, und wählen **öffnen**.  
   
   Die Datei wird im neuen, temporären Visual Studio-Projektmappe.

1. Starten Sie das Debuggen der app durch einen Ausführungsbefehl, z. B. Auswahl **Debuggen starten**, aus der **Debuggen** Menü.    
  
### <a name="to-import-an-app-into-an-existing-visual-studio-solution"></a>So importieren Sie eine app in einer vorhandenen Visual Studio-Projektmappe  
  
1.  Mit einem C++- C#, oder wählen Sie die Visual Basic-Projektmappe in Visual Studio öffnen **Datei** > **hinzufügen** > **vorhandenes Projekt**.  
  
1. In der **geöffneten Projekt** wählen Sie im Dialogfeld **alle Projektdateien**, sofern nicht bereits in der Dropdownliste neben ausgewählt, **Dateiname**.  
   
1. Navigieren Sie zu der *.exe* , wählen Sie ihn, und wählen **öffnen**.  
   
   Die Datei wird als ein neues Projekt unter der aktuellen Projektmappe angezeigt.  
   
1. Mit der neuen Datei ausgewählt, Debuggen Sie die app durch einen Ausführungsbefehl, z. B. Auswahl **Debuggen starten**, aus der **Debuggen** Menü.    
  
### <a name="see-also"></a>Siehe auch  
 [Debugger settings and preparation (Einstellungen und Vorbereitung des Debuggers)](../debugger/debugger-settings-and-preparation.md)   
 [Debugger security (Debuggersicherheit)](../debugger/debugger-security.md)   
 [DBG files (DBG-Dateien)](/previous-versions/visualstudio/visual-studio-2010/da528y14(v=vs.100))