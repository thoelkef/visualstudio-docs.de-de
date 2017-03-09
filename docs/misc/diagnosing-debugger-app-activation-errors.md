---
title: "Diagnose von Debugger-App-Aktivierungsfehlern | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.app_activation_failure"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 558ddc6d-0952-4617-84b8-0838717febcc
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "susanno"
manager: "douge"
---
# Diagnose von Debugger-App-Aktivierungsfehlern
Sie erhalten bei dem Versuch eine Windows Store\-App im Visual Studio\-Debugger zu starten möglicherweise einen der folgenden Fehler:  
  
 **8061**  
  
```  
Unable to activate Windows Store app 'AppName'. The ProcessName process started, but the activation request failed with error 'ErrorNumber'  
```  
  
 **8062**  
  
```  
Unable to activate Windows Store app 'AppName'. The activation request failed with error 'ErrorNumber'  
```  
  
## So diagnostizieren Sie diese Fehler  
 Es gibt keine sicheren Methoden zum Beheben dieser Fehler.  Verwenden Sie zum Ermitteln des Problems die folgenden Verfahren.  
  
### Ereignisanzeige verwenden  
  
1.  Ereignisanzeige öffnen \(suchen Sie im Windows\-Startmenü nach **Ereignisanzeige**.\)  Navigieren Sie in der Struktur der Ereignisanzeige zum Ordner **Anwendungs\- und Dienstprotokolle\\Microsoft\\Windows\\Apps**.  
  
2.  Filtern Sie die Ansicht zu Ereignis\-IDs: 5900 – 6000  
  
3.  Überprüfen Sie das Protokoll, und stellen Sie fest, was geschehen ist.  
  
### Verwenden des systemeigenen Debuggers  
 Konfigurieren Sie das Projekt für die Ausführung unter einem systemeigenen Debugger.  
  
 Legen Sie den **Debuggertyp** in Visual Studio auf der Seite **Debuggen** \(**Debugging** in C\+\+ und in JavaScript\) der Eigenschaftenseiten des Startprojekts auf **Nur systemeigen** fest.  
  
 Betrachten Sie die ausgelösten Ausnahmen im Ausgabefenster.  Sie sollten den Debugger so konfigurieren, dass er bei diesen Ausnahmen beendet wird.  
  
## Beheben von Lizenzierungsfehlern in Apps  
 Möglicherweise wird ein Aktivierungsfehler mit dem Text "Fehler beim Starten der App aufgrund eines Lizenzproblems" angezeigt. Probieren Sie die folgenden Problemumgehungen aus:  
  
-   Klicken Sie im Menü **Erstellen** auf **Projektmappe bereinigen**,öffnen Sie den Projektmappenordner im Datei\-Explorer und löschen Sie die Ordner **bin** und **obj**.  Klicken Sie anschließend auf **Erstellen**, **Projektmappe neu erstellen**.  Beim erneuten Erstellen der Projektmappe werden die entsprechenden Ordner neu erstellt.  
  
-   Wählen Sie die App im Startbildschirm aus und klicken Sie in der App\-Leiste auf "Deinstallieren".  Bereinigen Sie Ihre Projektmappe und erstellen Sie diese anschließend erneut.  
  
-   Verwenden Sie PowerShell\-Befehle in einer Eingabeaufforderung mit Admin\-Berechtigungen, um Ihre Entwicklerlizenz zu entfernen und neu zu installieren.  Bereinigen Sie Ihre Projektmappe und erstellen Sie diese anschließend erneut.  Siehe [Anfordern einer Entwicklerlizenz an einer Eingabeaufforderung](http://msdn.microsoft.com/library/windows/apps/hh974578.aspx#anfordern_einer_entwicklerlizenz_an_einer_eingabeaufforderung).