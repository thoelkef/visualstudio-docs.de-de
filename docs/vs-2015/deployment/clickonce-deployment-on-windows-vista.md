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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675474"
---
# <a name="clickonce-deployment-on-windows-vista"></a>ClickOnce-Bereitstellung unter Windows Vista
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Beim Entwickeln von Anwendungen in Visual Studio für die Benutzerkontensteuerung (User Account Control, UAC) unter Windows Vista wird normalerweise ein eingebettetes Manifest generiert, das als binäre XML-Daten in der ausführbaren Datei der Anwendung Da ClickOnce und com-Anwendungen ohne Registrierung ein externes Manifest erfordern, generiert Visual Studio eine Datei für diese Projekttypen, die die UAC-Daten anstelle eines eingebetteten Manifests enthalten. Standardmäßig verwendet Visual Studio Informationen aus einer Datei mit dem Namen "App. Manifest", um externe UAC-manifestressformationen (für die com-Bereitstellung von ClickOnce und Registrierung) zu generieren, oder um Sie in die ausführbare Datei der Anwendung einzubetten (für alle anderen Fälle). Visual Studio bietet die folgenden Optionen für die Generierung von Manifesten:  
  
- Verwenden Sie ein eingebettetes Manifest. Integrieren Sie UAC-Daten in die ausführbare Datei der Anwendung, und führen Sie Sie als normaler Benutzer aus.  
  
   Dies ist die Standardeinstellung (es sei denn, Sie verwenden ClickOnce). Diese Einstellung unterstützt die übliche Art und Weise, in der Visual Studio unter Windows Vista funktioniert. Das heißt, die Generierung eines internen und externen Manifests, das beide mit verwendet `AsInvoker` .  
  
- Verwenden Sie ein externes Manifest. Generieren eines externen Manifests mithilfe von "App. Manifest".  
  
   Dadurch wird nur das externe Manifest generiert, indem die Informationen in "App. Manifest" verwendet werden. Wenn Sie eine Anwendung mithilfe von ClickOnce oder com ohne Registrierung veröffentlichen, fügt Visual Studio dem Projekt "App. Manifest" hinzu und fügt diese Option hinzu.  
  
- Verwenden Sie kein Manifest. Erstellen Sie die Anwendung ohne ein Manifest.  
  
   Diese Vorgehensweise wird auch als *Virtualisierung*bezeichnet. Verwenden Sie diese Option, um die Kompatibilität mit vorhandenen Anwendungen früherer Versionen von Visual Studio zu verwenden.  
  
  Die neuen Eigenschaften sind auf der Seite **Anwendung** des Projekt-Designers (nur für Visual c#-Projekte) und im MSBuild-Projektdatei Format verfügbar.  
  
  Beachten Sie, dass die Methode zum Konfigurieren der Generierung von UAC-Manifesten in der Visual Studio-IDE abhängig vom Projekttyp (Visual c# und Visual Basic) abweicht.  
  
  Weitere Informationen zum Konfigurieren von Visual c#-Projekten für die Generierung von Manifesten finden Sie unter [Seite "Anwendung", Projekt-Designer (c#)](../ide/reference/application-page-project-designer-csharp.md).  
  
  Weitere Informationen zum Konfigurieren von Visual Basic Projekten für die Generierung von Manifesten finden Sie unter [Seite "Anwendung", Projekt-Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [ClickOnce-Sicherheit und-Bereitstellung](../deployment/clickonce-security-and-deployment.md)   
 [Benutzerberechtigungen und Visual Studio](https://msdn.microsoft.com/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [Seite "Anwendung", Projekt-Designer (c#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Seite „Anwendung“, Projekt-Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
