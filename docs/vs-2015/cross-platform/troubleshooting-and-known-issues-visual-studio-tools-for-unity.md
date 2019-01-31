---
title: Problembehandlung und bekannte Probleme (Visual Studio-Tools für Unity) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: troubleshooting
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
caps.latest.revision: 7
author: conceptdev
ms.author: crdun
manager: jillfra
ms.openlocfilehash: f614188d6a4a9855af072b200c71633ef7a2bd57
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54776841"
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>Problembehandlung und bekannte Probleme (Visual Studio-Tools für Unity)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
In diesem Abschnitt finden Sie Lösungen für häufige Probleme mit Visual Studio-Tools für Unity und Beschreibungen bekannter Probleme. Außerdem erfahren Sie, wie Sie Visual Studio-Tools für Unity verbessern können, indem Sie Fehler melden.  
  
## <a name="troubleshooting"></a>Problembehandlung  
 In den folgenden Abschnitten finden Sie Informationen zum Beheben häufiger Probleme mit Visual Studio-Tools für Unity.  
  
### <a name="migrating-from-unityvs-to-visual-studio-tools-for-unity"></a>Migrieren von UnityVS zu Visual Studio-Tools für Unity  
 Wenn Sie von UnityVS zu Visual Studio-Tools für Unity migrieren, müssen Sie neue Visual Studio-Projektmappen für Ihre Unity-Projekte generieren.  
  
##### <a name="to-migrate-your-unity-project-from-unityvs-18-to-visual-studio-tools-for-unity-19"></a>So migrieren Sie Ihr Unity-Projekt von UnityVS 1.8 zu Visual Studio-Tools für Unity 1.9  
  
1.  Löschen Sie die alten Projektmappen- und Projektdateien aus Ihrem Unity-Projekt. Suchen Sie im Stammverzeichnis Ihres Unity-Projekts die SLN- und PROJ-Dateien von Visual Studio, und löschen Sie alle.  
  
2.  Importieren Sie das Visual Studio-Tools für Unity-Paket in Ihr Unity-Projekt. Informationen zum Importieren des VSTU-Pakets finden Sie unter "Konfigurieren von Visual Studio-Tools für Unity" auf der Seite [Erste Schritte](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) .  
  
3.  Generieren Sie neue Projektmappen- und Projektdateien. Wenn Sie sie jetzt generieren möchten, klicken Sie im Unity-Editor im Hauptmenü auf **Visual Studio Tools**, **Generate Project Files**. Andernfalls können Sie diesen Schritt nach Wunsch überspringen. Visual Studio-Tools für Unity generiert die neuen Dateien automatisch, wenn Sie auf **Visual Studio Tools**, **Open in Visual Studio**klicken.  
  
### <a name="visual-studio-wont-load-the-solution-that-visual-studio-tools-for-unity-created"></a>Visual Studio lädt die Projektmappe nicht, die Visual Studio-Tools für Unity erstellt hat.  
 Weitere Informationen finden Sie unter [der Antwort auf diese Frage auf Stackoverflow](http://stackoverflow.com/a/24035907/36702).  
  
### <a name="on-windows-8-visual-studio-asks-to-download-the-unity-target-framework"></a>Unter Windows 8 fordert Visual Studio das Herunterladen des Unity-Zielframeworks an.  
 UnityVS erfordert .NET Framework 3.5, das nicht standardmäßig unter Windows 8 installiert ist. Um dieses Problem zu beheben, befolgen Sie die Anweisungen zum Herunterladen und Installieren von .NET Framework 3.5.  
  
## <a name="known-issues"></a>Bekannte Probleme  
 Es gibt bekannte Probleme in Visual Studio-Tools für Unity, deren Ursache die Interaktion des Debuggers mit der älteren Version von Unity des C#-Compilers ist. Wir arbeiten daran, diese Schwierigkeiten zu beheben, aber in der Zwischenzeit können die folgenden Probleme auftreten.  
  
-   Beim Debuggen stürzt Unity manchmal ab.  
  
-   Beim Debuggen friert Unity manchmal ein.  
  
-   Bei Einzel- und Prozedurschritten für Methoden kommt es mitunter zu einem Fehlverhalten, insbesondere bei Iteratoren oder innerhalb von Switch-Anweisungen.  
  
## <a name="reporting-errors"></a>Erstellen von Fehlerberichten  
 Helfen Sie uns, die Qualität von Visual Studio-Tools für Unity zu verbessern, indem Sie Fehlerberichte senden, sollte das Programm abstürzen, einfrieren oder ein anderer Fehler auftreten. Dies hilft uns beim Untersuchen und Beheben von Problemen in Visual Studio-Tools für Unity. Vielen Dank!  
  
### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Wie Sie einen Fehler melden, wenn Visual Studio einfriert  
 Uns wurde gemeldet, dass Visual Studio beim Debuggen mit Visual Studio-Tools für Unity mitunter einfriert, aber wir benötigen mehr Daten, um dieses Problem zu verstehen. Sie können uns bei der Untersuchung helfen, indem Sie die folgenden Schritte ausführen.  
  
##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>So melden Sie, dass Visual Studio beim Debuggen mit Visual Studio-Tools für Unity einfriert  
  
1. Öffnen Sie eine Instanz von Visual Studio.  
  
2. Öffnen Sie das Dialogfeld "An den Prozess anhängen". Wählen Sie in der neuen Instanz von Visual Studio im Hauptmenü **Debuggen**, **An den Prozess anhängen**.  
  
3. Hängen Sie den Debugger an die eingefrorene Instanz von Visual Studio an. Wählen Sie im Dialogfeld **An den Prozess anhängen** die eingefrorene Instanz von Visual Studio in der Tabelle **Verfügbare Prozesse** aus, und klicken Sie dann auf die Schaltfläche **Anhängen** .  
  
4. Halten Sie den Debugger an. Wählen Sie in der neuen Instanz von Visual Studio im Hauptmenü **Debuggen**, **Alle unterbrechen** , oder drücken Sie **STRG+ALT+PAUSE**.  
  
5. Erstellen Sie einen Thread-Dump. Geben Sie an der Eingabeaufforderung den folgenden Befehl ein, und drücken Sie die **EINGABETASTE**.  
  
   ```powershell  
   Debug.ListCallStack /AllThreads /ShowExternalCode  
   ```  
  
    Möglicherweise müssen Sie zuerst das Fenster **Befehl** einblenden. Wählen Sie in Visual Studio im Hauptmenü **Ansicht**, **Weitere Fenster**, **Befehlsfenster**.  
  
6. Senden Sie zum Schluss den Thread-Dump an [vstusp@microsoft.com](mailto:vstusp@microsoft.com)zusammen mit einer Beschreibung, was Sie gerade getan haben, als Visual Studio eingefroren ist.
