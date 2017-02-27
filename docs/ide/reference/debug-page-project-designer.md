---
title: "Seite &quot;Debuggen&quot;, Projekt-Designer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesDebug"
helpviewer_keywords: 
  - "Projekt-Designer, Seite „Debuggen“"
  - "Seite „Debuggen“ im Projekt-Designer"
ms.assetid: ef11eae9-df96-4e20-aabd-2678ba317140
caps.latest.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Seite &quot;Debuggen&quot;, Projekt-Designer
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!WARNING]
>  Dieses Thema gilt nicht für Windows Store\-Apps zu.  Siehe [Starten einer Debugsitzung \(VB, C\#, C\+\+ und XAML\)](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) im Windows Developer Center.  
  
 Verwenden Sie die Seite **DebuggenProjekt\-Designer**, um Eigenschaften für das Debuggen des Verhaltens in einem Visual Basic\- oder C\#\-Projekt festzulegen.  
  
 Um auf die Seite **Debuggen** zuzugreifen, wählen Sie einen Projektknoten in **Projektmappen\-Explorer** aus.  Klicken Sie im Menü **Projekt** wählen Sie *Projektname***Eigenschaften** aus.  Wenn **Projekt\-Designer** angezeigt wird, klicken Sie auf die Registerkarte **Debuggen**.  
  
## Konfiguration und Plattform  
 Die folgenden Optionen ermöglichen es Ihnen, die anzuzeigende bzw. zu ändernde Konfiguration und Plattform auszuwählen.  
  
 **Konfiguration**  
 Gibt an, welche Konfigurationseinstellungen angezeigt oder geändert werden sollen.  Die Einstellungen können **Debuggen** \(Standard\), **Version** oder **Alle Konfigurationen** sein.  Weitere Informationen finden Sie unter [Debug and Release Project Configurations](http://msdn.microsoft.com/de-de/0440b300-0614-4511-901a-105b771b236e).  
  
 **Plattform**  
 Gibt an, welche Plattformeinstellungen angezeigt oder geändert werden sollen.  Die Optionen können **Any CPU** \(Standard\), **x64** und **x86** enthalten.  Weitere Informationen finden Sie unter [Debug and Release Project Configurations](http://msdn.microsoft.com/de-de/0440b300-0614-4511-901a-105b771b236e).  
  
## Startaktion  
 **Startaktion** gibt das beim Debuggen der Anwendung zu startende Element an: das Projekt, ein benutzerdefiniertes Programm, eine URL oder nichts.  Standardmäßig ist diese Option auf **Projekt starten** festgelegt.  **Startaktion**, das auf der Seite **Debuggen** festgelegt wird, bestimmt den Wert der \- Eigenschaft `StartAction`.  
  
 **Projekt starten**  
 Wählen Sie diese Option aus, um anzugeben, dass die ausführbare Datei \(für Windows\-basierte Anwendung und Konsolenanwendungsprojekte\) gestartet werden soll, wenn die Anwendung debuggt wird.  Diese Option ist standardmäßig aktiviert.  
  
 **Externes Programm starten**  
 Wählen Sie diese Option aus, um anzugeben, dass ein bestimmtes Programm gestartet werden soll, wenn die Anwendung debuggt wird.  
  
 **Browser mit folgender URL starten**  
 Wählen Sie diese Option aus, um anzugeben, dass auf eine bestimmte URL zugegriffen werden soll, wenn die Anwendung debuggt wird.  
  
## Starten von Optionen  
 **Befehlszeilenargumente**  
 Geben Sie in dieses Textfeld die Befehlszeilenargumente zum Debuggen ein.  
  
 **Arbeitsverzeichnis**  
 Geben Sie in diesem Textfeld das Verzeichnis ein, von dem aus das Projekt gestartet wird.  Oder klicken Sie auf die Schaltfläche zum Durchsuchen \(**...**\) um ein Verzeichnis auszuwählen.  
  
 **Remoten Computer verwenden**  
 Um die Anwendung von einem Remotecomputer zu debuggen, wählen Sie dieses Kontrollkästchen und geben Sie den Pfad zum Remotecomputer im Textfeld ein.  
  
## Aktivieren von Debuggern  
 **Nicht verwaltetes Codedebuggen aktivieren**  
 Diese Option gibt an, ob das Debuggen des systemeigenen Codes unterstützt wird.  Aktivieren Sie dieses Kontrollkästchen, wenn Sie COM\-Objekte ausführen, oder wenn Sie ein benutzerdefiniertes Programm starten, das in systemeigenem Code geschrieben wird, der das Projekt aufruft und Sie den systemeigenen Code debuggen müssen.  Deaktivieren Sie dieses Kontrollkästchen, um das Debuggen von nicht verwaltetem Code zu deaktivieren.  Dieses Kontrollkästchen ist standardmäßig deaktiviert.  
  
 **SQL Server\-Debuggen aktivieren**  
 Aktivieren oder deaktivieren Sie dieses Kontrollkästchen, um das Debuggen von SQL\-Prozeduren aus der Visual Basic\-Anwendung zu aktivieren oder zu deaktivieren.  Dieses Kontrollkästchen ist standardmäßig deaktiviert.  
  
 **Visual Studio\-Hostprozess aktivieren**  
 Aktivieren Sie dieses Kontrollkästchen, um den Visual Studio\-Hostprozess zu aktivieren.  Dieses Kontrollkästchen ist standardmäßig aktiviert.  Weitere Informationen finden Sie unter [Hostprozess \(vshost.exe\)](../../ide/hosting-process-vshost-exe.md).  
  
 Um in einer Sicherheitszone zu debuggen, müssen Sie diese Option **Diese Anwendung mit dem ausgewählten Berechtigungssatz debuggen** und in [Dialogfeld "Erweiterte Sicherheitseinstellungen"](../../ide/reference/advanced-security-settings-dialog-box.md) aktivieren.  
  
## Siehe auch  
 [Debuggen in Visual Studio](../../debugger/debugging-in-visual-studio.md)   
 [Projekteinstellungen für C\#\-Debugkonfigurationen](../../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Projekteinstellungen für eine Visual Basic\-Debugkonfiguration](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Managing Debugging Properties](http://msdn.microsoft.com/de-de/92474d16-e7fe-4fac-9287-6bd6b3a7eb68)   
 [Gewusst wie: Debuggen einer ClickOnce\-Anwendung mit eingeschränkten Berechtigungen](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Gewusst wie: Erstellen und Bearbeiten von Konfigurationen](../../ide/how-to-create-and-edit-configurations.md)