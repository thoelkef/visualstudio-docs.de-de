---
title: ClickOnce-Bereitstellung unter Windows Vista | Microsoft Docs
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
ms.openlocfilehash: c546d7e4287fc47a3770baa306a43a1631be2f06
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
ms.locfileid: "31558931"
---
# <a name="clickonce-deployment-on-windows-vista"></a>ClickOnce-Bereitstellung unter Windows Vista
Erstellen von Anwendungen in Visual Studio codiert für die Benutzerkontensteuerung (UAC) unter Windows Vista normalerweise kein eingebettetes Manifest generiert als binäre XML-Daten in die ausführbare Datei der Anwendung. Da ClickOnce und COM ohne Registrierung Anwendungen ein externes Manifest erforderlich sind, generiert Visual Studio eine Datei für diese Typen von Projekten, die die UAC-Daten, anstatt ein eingebettetes Manifest enthält. Standardmäßig verwendet Visual Studio Informationen aus einer Datei namens app.manifest, zum Generieren von externen UAC-Manifestinformationen (für die Bereitstellung von ClickOnce und COM ohne Registrierung) oder zum Einbetten in ausführbaren Anwendungsdatei (bei allen anderen Fällen). Visual Studio bietet die folgenden Optionen für die manifestgenerierung auf:  
  
-   Verwenden Sie kein eingebettetes Manifest. Betten Sie UAC-Daten in die ausführbare Datei der Anwendung, und als normaler Benutzer ausführen.  
  
     Dies ist die Standardeinstellung (es sei denn, Sie mithilfe von ClickOnce). Diese Einstellung unterstützt die übliche Weise, in der Visual Studio funktioniert, auf Windows Vista; d. h. die Generierung von einem internen und externen Manifest, beide mit `AsInvoker`.  
  
-   Verwenden Sie ein externes Manifest. Generieren Sie ein externes Manifest mithilfe von app.manifest.  
  
     Dadurch wird nur auf das externe Manifest anhand der Informationen in app.manifest generiert. Wenn Sie eine Anwendung mithilfe von ClickOnce oder COM ohne Registrierung veröffentlichen, wird Visual Studio app.manifest zum Projekt hinzugefügt und fügt diese Option aus.  
  
-   Verwenden Sie kein Manifest. Erstellen Sie die Anwendung ohne Manifest.  
  
     Diese Vorgehensweise ist auch bekannt als *Virtualisierung*. Verwenden Sie diese Option, um die Kompatibilität mit vorhandenen Anwendungen aus früheren Versionen von Visual Studio.  
  
 Die neuen Eigenschaften stehen auf der **Anwendung** Seite im Projekt-Designer (für Visual C#-Projekte nur) und in der MSBuild-Projektdateiformat.  
  
 Beachten Sie, dass die Methode zum Konfigurieren von UAC-manifestgenerierung in Visual Studio-IDE je nach Projekttyp (Visual c# und Visual Basic) unterscheidet.  
  
 Informationen zum Konfigurieren von Visual C#-Projekten zur Generierung von Manifesten finden Sie unter [Anwendungsseite, Projekt-Designer (c#)](../ide/reference/application-page-project-designer-csharp.md).  
  
 Informationen zum Konfigurieren von Visual Basic-Projekten zur Generierung von Manifesten finden Sie unter [Anwendungsseite, Projekt-Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Sicherheit und -Bereitstellung](../deployment/clickonce-security-and-deployment.md)   
 [Benutzerberechtigungen und Visual Studio](http://msdn.microsoft.com/en-us/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [Seite „Anwendung“, Projekt-Designer (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Seite „Anwendung“, Projekt-Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)