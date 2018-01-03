---
title: "Seite „Debuggen“, Projekt-Designer | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vb.ProjectPropertiesDebug
helpviewer_keywords:
- Project Designer, Debug page
- Debug page in Project Designer
ms.assetid: ef11eae9-df96-4e20-aabd-2678ba317140
caps.latest.revision: "32"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a16f39d9f9ba6c3e0790a53c85d0824178083953
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="debug-page-project-designer"></a>Seite "Debuggen", Projekt-Designer
> [!WARNING]
>  Dieses Thema gilt nicht für UWP-Apps. Weitere Informationen finden Sie im Windows Dev Center unter [Start a debugging session for a UWP app in Visual Studio (VB, C#, C++ and XAML) (Starten einer Debugsitzung für eine UWP-App in Visual Studio (VB, C#, C++ und XAML))](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).  
  
 Verwenden Sie die Seite **Debuggen** des **Projekt-Designers**, um Eigenschaften für das Debugverhalten in einem Visual Basic oder C#-Projekt festzulegen.  
  
 Klicken Sie auf einen Projektknoten im **Projektmappen-Explorer**, um auf die Seite **Debuggen** zuzugreifen. Klicken Sie im Menü **Projekt** auf *Projektname***Eigenschaften**. Sobald der **Projekt-Designer** angezeigt wird, klicken Sie auf die Registerkarte **Debuggen**.  
  
## <a name="configuration-and-platform"></a>Konfiguration und Plattform  
 Die folgenden Optionen ermöglichen es Ihnen, die anzuzeigende bzw. zu ändernde Konfiguration und Plattform auszuwählen.  
  
 **Konfiguration**  
 Gibt an, welche Konfigurationseinstellungen angezeigt oder geändert werden sollen. Die Einstellungen sind **Debuggen** (Standardeinstellung), **Freigeben** oder **Alle Konfigurationen**. Weitere Informationen finden Sie unter [Debug- und Releaseprojektkonfigurationen](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
 **Plattform**  
 Gibt an, welche Plattformeinstellungen angezeigt oder geändert werden sollen. Die Optionen sind **Beliebige CPU** (Standardeinstellung), **x64** oder **x86**. Weitere Informationen finden Sie unter [Debug- und Releaseprojektkonfigurationen](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
## <a name="start-action"></a>Startvorgang  
 Der **Startvorgang** gibt an, welches Element beim Debuggen der Anwendung gestartet wird: das Projekt, ein benutzerdefiniertes Programm, eine URL oder keines. Diese Option ist standardmäßig auf **Projekt starten** festgelegt. Die Einstellung **Startaktion** auf der Seite **Debuggen** bestimmt den Wert der `StartAction`-Eigenschaft.  
  
 **Projekt starten**  
 Wählen Sie diese Option aus, um anzugeben, dass die ausführbare Datei (bei Projekten für Windows-Anwendungen und Konsolenanwendungen) beim Debuggen der Anwendung gestartet werden soll. Diese Option ist standardmäßig ausgewählt.  
  
 **Externes Programm starten**  
 Wählen Sie diese Option aus, um anzugeben, dass ein bestimmtes Programm beim Debuggen der Anwendung gestartet werden soll.  
  
 **Browser mit URL starten**  
 Wählen Sie diese Option aus, um anzugeben, dass beim Debuggen der Anwendung auf eine bestimmte URL zugegriffen werden soll.  
  
## <a name="start-options"></a>Startoptionen  
 **Befehlszeilenargumente**  
 Geben Sie in diesem Textfeld die Befehlszeilenargumente ein, die für das Debuggen verwendet werden sollen.  
  
 **Arbeitsverzeichnis**  
 Geben Sie in diesem Textfeld das Verzeichnis ein, aus dem das Projekt gestartet wird. Klicken Sie alternativ auf die Schaltfläche „Durchsuchen“ (**...**), um ein Verzeichnis auszuwählen.  
  
 **Remotecomputer verwenden**  
 Aktivieren Sie dieses Kontrollkästchen, und geben Sie den Pfad zum Remotecomputer in das Textfeld ein, um die Anwendung über einen Remotecomputer zu debuggen.  
  
## <a name="enable-debuggers"></a>Debugger aktivieren  
 **Nicht verwaltetes Codedebuggen aktivieren**  
 Diese Option gibt an, ob das Debuggen von nativem Code unterstützt wird. Aktivieren Sie dieses Kontrollkästchen, wenn Sie COM-Objekte aufrufen, oder wenn Sie ein benutzerdefiniertes Programm starten, das Ihr Projekt aufruft und in nativem Code geschrieben ist, und Sie den nativen Code debuggen müssen. Deaktivieren Sie dieses Kontrollkästchen, um das Debuggen von unverwaltetem Code zu deaktivieren. Dieses Kontrollkästchen ist standardmäßig deaktiviert.  
  
 **SQL Server-Debuggen aktivieren**  
 Aktivieren oder deaktivieren Sie dieses Kontrollkästchen, um das Debuggen von SQL-Prozeduren über Ihre Visual Basic-Anwendung zu aktivieren oder zu deaktivieren. Dieses Kontrollkästchen ist standardmäßig deaktiviert.  
  
 **Visual Studio-Hostprozess aktivieren**  
 Aktivieren Sie dieses Kontrollkästchen, um den Visual Studio-Hostprozess zu aktivieren. Dieses Kontrollkästchen ist standardmäßig aktiviert. Weitere Informationen finden Sie unter [Hostprozess („vshost.exe“)](../../ide/hosting-process-vshost-exe.md).  
  
 Sie müssen diese Option und **Diese Anwendung mit dem ausgewählten Berechtigungssatz debuggen** im Dialogfeld [Erweiterte Sicherheitseinstellungen](../../ide/reference/advanced-security-settings-dialog-box.md) aktivieren, um in einer Sicherheitszone zu debuggen.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen in Visual Studio](../../debugger/debugging-in-visual-studio.md)   
 [Project Settings for  C# Debug Configurations (Projekteinstellungen für C#-Debugkonfigurationen)](../../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Project Settings for a Visual Basic Debug Configuration (Projekteinstellungen für eine Visual Basic-Debugkonfiguration)](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Verwalten von Debugeigenschaften](http://msdn.microsoft.com/en-us/92474d16-e7fe-4fac-9287-6bd6b3a7eb68)   
 [How to: Debug a ClickOnce Application with Restricted Permissions (Vorgehensweise: Debuggen einer ClickOnce-Anwendung mit eingeschränkten Berechtigungen)](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Gewusst wie: Erstellen und Bearbeiten von Konfigurationen](../../ide/how-to-create-and-edit-configurations.md)