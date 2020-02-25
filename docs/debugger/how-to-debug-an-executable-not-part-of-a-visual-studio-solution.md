---
title: Debuggen einer APP, die nicht Teil einer Visual Studio-Projekt Mappe ist
titleSuffix: ''
ms.custom: ''
ms.date: 02/21/2020
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 740af718a2928991d46bedbd6709337b9b20a254
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557915"
---
# <a name="debug-an-app-that-isnt-part-of-a-visual-studio-solution-c-c-visual-basic-f"></a>Debuggen einer APP, die nicht Teil einer Visual StudioC++- C#Projekt Mappe ist F#(,, Visual Basic,)

Möglicherweise möchten Sie eine APP (*exe* -Datei) Debuggen, die nicht Teil einer Visual Studio-Projekt Mappe ist. Möglicherweise handelt es sich um ein [geöffnetes Ordner](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) Projekt, oder Sie oder eine andere Person haben die APP außerhalb von Visual Studio erstellt, oder Sie haben die APP von einem anderen Ort aus erstellt.

- Informationen zu einem geöffneten Ordner Projekt in Visual Studio (ohne Projekt-oder Projektmappendatei) finden [Sie unter Ausführen und Debuggen von Code](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md#run-and-debug-your-code) oder unter Konfigurieren von C++ [debuggingparametern mit "Launch. vs. JSON](/cpp/build/open-folder-projects-cpp#configure-debugging-parameters-with-launchvsjson)".

- Für eine APP, die nicht in Visual Studio vorhanden ist, besteht die übliche Möglichkeit zum Debuggen darin, die APP außerhalb von Visual Studio zu starten und dann mithilfe von anfügen **an den Prozess** im Visual Studio-Debugger anzufügen. Weitere Informationen finden Sie unter [Anfügen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

   Das Anfügen an eine APP erfordert manuelle Schritte, die einige Sekunden in Anspruch nehmen. Aufgrund dieser Verzögerung unterstützt das Anfügen nicht das Debuggen eines Start Problems, oder eine APP, die nicht auf Benutzereingaben wartet und schnell beendet wird.

   In diesen Fällen können Sie ein Visual Studio-exe-Projekt für die APP erstellen oder es in eine vorhandene C#, Visual Basic oder C++ Projekt Mappe importieren. EXE-Projekte werden nicht von allen Programmiersprachen unterstützt.

>[!IMPORTANT]
>Debuggingfunktionen für eine APP, die nicht in Visual Studio erstellt wurde, sind begrenzt, egal, ob Sie an die APP anfügen oder Sie einer Visual Studio-Projekt Mappe hinzufügen
>
>Wenn Sie über den Quellcode verfügen, empfiehlt es sich, den Code in ein Visual Studio-Projekt zu importieren. Führen Sie dann einen Debugbuild der APP aus.
>
>Wenn Sie nicht über den Quellcode verfügen und die APP keine [Debuginformationen](../debugger/how-to-set-debug-and-release-configurations.md) in einem kompatiblen Format aufweist, sind die verfügbaren Debuggingfeatures sehr gering.

### <a name="to-create-a-new-exe-project-for-an-existing-app"></a>So erstellen Sie ein neues exe-Projekt für eine vorhandene App

1. Wählen Sie in Visual Studio **Datei** >  > **Projekt** **Öffnen** aus.

1. Wählen Sie im Dialogfeld **Projekt öffnen** in der Dropdown Liste neben **Dateiname**die Option **alle Projektdateien**aus, sofern diese nicht bereits ausgewählt ist.

1. Navigieren Sie zur *exe* -Datei, wählen Sie Sie aus, und klicken Sie auf **Öffnen**.

   Die Datei wird in einer neuen temporären Visual Studio-Projekt Mappe angezeigt.

1. Starten Sie das Debuggen der APP, indem Sie im Menü **Debuggen** einen Ausführungs Befehl wie **Debuggen starten**auswählen.

### <a name="to-import-an-app-into-an-existing-visual-studio-solution"></a>So importieren Sie eine app in eine vorhandene Visual Studio-Projekt Mappe

1. Wenn eine C++- C#,-oder-Visual Basic Projekt Mappe in Visual Studio geöffnet ist, wählen Sie **Datei** >  > **vorhandenes Projekt** **Hinzufügen** aus.

1. Wählen Sie im Dialogfeld **Projekt öffnen** in der Dropdown Liste neben **Dateiname**die Option **alle Projektdateien**aus, sofern diese nicht bereits ausgewählt ist.

1. Navigieren Sie zur *exe* -Datei, wählen Sie Sie aus, und klicken Sie auf **Öffnen**.

   Die Datei wird als neues Projekt unter der aktuellen Projekt Mappe angezeigt.

1. Wenn die neue Datei ausgewählt ist, starten Sie das Debugging der APP, indem Sie im Menü **Debuggen** einen Ausführungs Befehl wie z. b. **Debuggen starten**auswählen

### <a name="see-also"></a>Weitere Informationen
- [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)
- [Debuggersicherheit](../debugger/debugger-security.md)
- [DBG files (DBG-Dateien)](/previous-versions/visualstudio/visual-studio-2010/da528y14(v=vs.100))