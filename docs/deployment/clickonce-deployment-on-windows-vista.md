---
title: ClickOnce-Bereitstellung unter Windows Vista | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- UAC manifest generation
- ClickOnce deployment, Windows
- manifest generation
- Windows, ClickOnce deployment
ms.assetid: b21a0ebc-0ff6-4f49-8993-7d1ad3f8cac2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0389665349ae9c39a0f820bc047af6cc4db2b683
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49867532"
---
# <a name="clickonce-deployment-on-windows-vista"></a>ClickOnce-Bereitstellung unter Windows Vista

Erstellen von Anwendungen in Visual Studio, für die Benutzerkontensteuerung (UAC) unter Windows Vista normalerweise ein eingebettetes Manifest, generiert codiert als binary XML-Daten in die ausführbare Datei der Anwendung.  ClickOnce und registrierungsfreiem COM-Anwendungen erfordern ein externes Manifest, damit Visual Studio eine Datei für diese Projekte mit den UAC-Daten, statt ein eingebettetes Manifest generiert wird. Für ClickOnce und registrierungsfreiem COM-Bereitstellungen, verwendet Visual Studio Informationen aus einer Datei namens *"App.manifest"* zum Generieren externer UAC-Manifestinformationen. In allen anderen Fällen bettet Visual Studio die UAC-Daten in die ausführbare Datei der Anwendung. 

Visual Studio bietet die folgenden Optionen für die manifestgenerierung auf:  
  
- Verwenden Sie ein eingebettetes Manifest. UAC-Daten in die ausführbare Datei der Anwendung einbetten, und als ein normaler Benutzer ausführen.  
  
   Dies ist die Standardeinstellung (es sei denn, Sie ClickOnce verwenden). Diese Einstellung unterstützt die übliche Weise, in der Visual Studio funktioniert, unter Windows Vista, mit der Generierung von einer internen und ein externes Anwendungsmanifest mit `AsInvoker`.  
  
- Verwenden Sie ein externes Manifest. Generieren Sie ein externes Manifest mit *"App.manifest"*.  
  
   Dadurch wird nur auf das externe Manifest generiert, mit den Informationen in *"App.manifest"*. Wenn Sie eine Anwendung mit ClickOnce oder COM ohne Registrierung veröffentlichen, fügt Visual Studio *"App.manifest"* auf das Projekt und fügt dann diese Option aus.  
  
- Verwenden Sie kein Manifest. Erstellen Sie die Anwendung ohne Manifest.  
  
   Dieser Ansatz ist auch bekannt als *Virtualisierung*. Verwenden Sie diese Option für die Kompatibilität mit vorhandenen Anwendungen aus früheren Versionen von Visual Studio.  
  
  Die neuen Eigenschaften stehen auf der **Anwendung** Seite, Projekt-Designer (Visual C# -Code nur für Projekte) und in das MSBuild-Projektdateiformat.  
  
  Die Methode zum Konfigurieren von UAC-manifestgenerierung in Visual Studio-IDE unterscheidet sich je nach Projekttyp (Visual c# oder Visual Basic).  
  
  * Informationen zum Konfigurieren von Visual C#-Projekten zur Generierung von Manifesten finden Sie unter [Anwendungsseite, Projekt-Designer (c#)](../ide/reference/application-page-project-designer-csharp.md).  
  
  * Informationen zum Konfigurieren von Visual Basic-Projekte zur Generierung von Manifesten finden Sie unter [Anwendungsseite, Projekt-Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Sicherheit und Bereitstellung](../deployment/clickonce-security-and-deployment.md)   
 [Benutzerberechtigungen und Visual Studio](https://msdn.microsoft.com/library/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [Seite „Anwendung“, Projekt-Designer (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Seite „Anwendung“, Projekt-Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)