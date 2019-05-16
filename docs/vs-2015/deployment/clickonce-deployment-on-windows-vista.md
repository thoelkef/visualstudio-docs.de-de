---
title: ClickOnce-Bereitstellung unter Windows Vista | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e25f9da960b1de8acb1950b2bdd3ab7e61409f17
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65675474"
---
# <a name="clickonce-deployment-on-windows-vista"></a>ClickOnce-Bereitstellung unter Windows Vista
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Erstellen von Anwendungen in Visual Studio, für die Benutzerkontensteuerung (UAC) unter Windows Vista normalerweise ein eingebettetes Manifest, generiert codiert als binary XML-Daten in die ausführbare Datei der Anwendung. Da ClickOnce und registrierungsfreiem COM-Anwendungen ein externes Manifest erforderlich sind, generiert Visual Studio eine Datei für diese Arten von Projekten, die mit den UAC-Daten, statt ein eingebettetes Manifest an. Standardmäßig verwendet Visual Studio Informationen aus einer Datei namens "App.manifest", zum Generieren von externen UAC-Manifestinformationen (für die Bereitstellung von ClickOnce und registrierungsfreiem COM) oder um sie in der Anwendung die ausführbare Datei (bei allen anderen Fällen) einbetten. Visual Studio bietet die folgenden Optionen für die manifestgenerierung auf:  
  
- Verwenden Sie ein eingebettetes Manifest. UAC-Daten in die ausführbare Datei der Anwendung einbetten, und als normaler Benutzer ausführen.  
  
   Dies ist die Standardeinstellung (es sei denn, Sie ClickOnce verwenden). Diese Einstellung unterstützt die übliche Weise, in der Visual Studio funktioniert, unter Windows Vista; d. h. die Generierung von einer internen und externen Manifest mit `AsInvoker`.  
  
- Verwenden Sie ein externes Manifest. Generieren Sie ein externes Manifest mithilfe von "App.manifest" ein.  
  
   Dadurch wird nur auf das externe Manifest mithilfe der Informationen in "App.manifest" generiert. Wenn Sie eine Anwendung mit ClickOnce oder COM ohne Registrierung veröffentlichen, wird Visual Studio dem Projekt "App.manifest" hinzugefügt und fügt diese Option.  
  
- Verwenden Sie kein Manifest. Erstellen Sie die Anwendung ohne Manifest.  
  
   Dieser Ansatz ist auch bekannt als *Virtualisierung*. Verwenden Sie diese Option für die Kompatibilität mit vorhandenen Anwendungen aus früheren Versionen von Visual Studio.  
  
  Die neuen Eigenschaften stehen auf der **Anwendung** Seite, Projekt-Designer (Visual C# -Code nur für Projekte) und in das MSBuild-Projektdateiformat.  
  
  Beachten Sie, dass die Methode zum Konfigurieren von UAC-manifestgenerierung in Visual Studio-IDE, je nach Projekttyp (Visual c# und Visual Basic unterscheidet).  
  
  Informationen zum Konfigurieren von Visual C#-Projekten zur Generierung von Manifesten finden Sie unter [Anwendungsseite, Projekt-Designer (c#)](../ide/reference/application-page-project-designer-csharp.md).  
  
  Informationen zum Konfigurieren von Visual Basic-Projekte zur Generierung von Manifesten finden Sie unter [Anwendungsseite, Projekt-Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Sicherheit und -Bereitstellung](../deployment/clickonce-security-and-deployment.md)   
 [Benutzerberechtigungen und Visual Studio](https://msdn.microsoft.com/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [Seite „Anwendung“, Projekt-Designer (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Seite „Anwendung“, Projekt-Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
