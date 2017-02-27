---
title: "ClickOnce Deployment on Windows Vista | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "UAC manifest generation"
  - "ClickOnce deployment, Windows"
  - "manifest generation"
  - "Windows, ClickOnce deployment"
ms.assetid: b21a0ebc-0ff6-4f49-8993-7d1ad3f8cac2
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# ClickOnce Deployment on Windows Vista
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Beim Erstellen von Anwendungen in Visual Studio für die Benutzerkontensteuerung \(User Account Control, UAC\) unter Windows Vista wird normalerweise ein eingebettetes Manifest generiert, das in Form von XML\-Binärdaten in der ausführbaren Datei der Anwendung kodiert wird.  Da ClickOnce\-Anwendungen und COM\-Anwendungen ohne Registrierung ein externes Manifest erfordern, generiert Visual Studio bei diesen Projekttypen anstelle des eingebetteten Manifests eine Datei, die die UAC\-Daten enthält.  Standardmäßig verwendet Visual Studio Informationen aus einer Datei namens app.manifest, um \(bei ClickOnce\-Bereitstellung oder COM\-Bereitstellung ohne Registrierung\) externe UAC\-Manifestinformationen zu generieren oder um sie \(in allen anderen Fällen\) in die ausführbare Datei der Anwendung einzubetten.  Visual Studio bietet folgende Optionen zur Generierung von Manifesten:  
  
-   Verwenden Sie ein eingebettetes Manifest.  Betten Sie die UAC\-Daten in die ausführbare Datei der Anwendung ein, und führen Sie sie als normaler Benutzer aus.  
  
     Dies ist die Standardeinstellung \(außer bei Verwendung von ClickOnce\).  Diese Einstellung unterstützt die übliche Art und Weise, in der Visual Studio unter Windows Vista arbeitet \(d. h. die Generierung sowohl eines internen als auch eines externen Manifests mittels `AsInvoker`\).  
  
-   Verwenden Sie ein externes Manifest.  Generieren Sie ein externes Manifest mithilfe der Datei app.manifest.  
  
     Hierbei wird ausschließlich das externe Manifest mit den Informationen aus app.manifest generiert.  Wenn Sie eine Anwendung mittels ClickOnce oder COM ohne Registrierung veröffentlichen, fügt Visual Studio app.manifest zum Projekt hinzu, und fügt diese Option hinzu.  
  
-   Verwenden Sie kein Manifest.  Erstellen Sie die Anwendung ohne ein Manifest.  
  
     Dieser Ansatz wird auch als *Virtualisierung* bezeichnet.  Verwenden Sie diese Option, wenn Sie Kompatibilität mit vorhandenen Anwendungen aus früheren Visual Studio\-Versionen erreichen möchten.  
  
 Die neuen Eigenschaften sind auf der Seite **Anwendung** im Projekt\-Designer \(nur bei Visual C\#\-Projekten\) und im MSBuild\-Projektdateiformat verfügbar.  
  
 Beachten Sie, dass sich die Methode zum Konfigurieren der Generierung von UAC\-Manifesten in der Visual Studio\-Entwicklungsumgebung nach dem Projekttyp richtet \(Visual C\# und Visual Basic\).  
  
 Informationen zum Konfigurieren von Visual C\#\-Projekten zur Generierung von Manifesten finden Sie unter [Seite "Anwendung", Projekt\-Designer \(C\#\)](../ide/reference/application-page-project-designer-csharp.md).  
  
 Informationen zum Konfigurieren von Visual Basic\-Projekten zur Generierung von Manifesten finden Sie unter [Seite "Anwendung", Projekt\-Designer \(Visual Basic\)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
## Siehe auch  
 [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md)   
 [User Permissions and Visual Studio](http://msdn.microsoft.com/de-de/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [Seite "Anwendung", Projekt\-Designer \(C\#\)](../ide/reference/application-page-project-designer-csharp.md)   
 [Seite "Anwendung", Projekt\-Designer \(Visual Basic\)](../ide/reference/application-page-project-designer-visual-basic.md)