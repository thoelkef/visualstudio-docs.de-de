---
title: ClickOnce-Bereitstellung unter Windows Vista | Microsoft-Dokumentation
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b76804eb8c06acbcdeac017108773056ee38338
ms.sourcegitcommit: 1803a67b516f67b209d8f4cf147314e604ef1927
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2020
ms.locfileid: "89641497"
---
# <a name="clickonce-deployment-on-windows-vista"></a>ClickOnce-Bereitstellung unter Windows Vista

Beim Entwickeln von Anwendungen in Visual Studio für die Benutzerkontensteuerung (User Account Control, UAC) unter Windows Vista wird normalerweise ein eingebettetes Manifest generiert, das als binäre XML-Daten in der ausführbaren Datei der Anwendung  ClickOnce-und Registrierungs freie com-Anwendungen erfordern ein externes Manifest, sodass Visual Studio eine Datei für diese Projekte generiert, die die UAC-Daten anstelle eines eingebetteten Manifests enthält. Bei ClickOnce-und Registrierungs losen com-bereit Stellungen verwendet Visual Studio Informationen aus einer Datei mit dem Namen " *app. Manifest* ", um Informationen zu externen UAC-Manifesten zu generieren. In allen anderen Fällen bettet Visual Studio die UAC-Daten in die ausführbare Datei der Anwendung ein.

Visual Studio bietet die folgenden Optionen für die Generierung von Manifesten:

- Verwenden Sie ein eingebettetes Manifest. Betten Sie UAC-Daten in die ausführbare Datei der Anwendung ein, und führen Sie Sie als normaler Benutzer aus.

   Dies ist die Standardeinstellung (es sei denn, Sie verwenden ClickOnce). Diese Einstellung unterstützt die übliche Art und Weise, in der Visual Studio unter Windows Vista funktioniert, mit der Generierung eines internen und eines externen Manifests mithilfe von `AsInvoker` .

- Verwenden Sie ein externes Manifest. Generieren eines externen Manifests mithilfe von " *app. Manifest*".

   Dadurch wird nur das externe Manifest generiert, indem die Informationen in " *app. Manifest*" verwendet werden. Wenn Sie eine Anwendung mithilfe von ClickOnce oder com ohne Registrierung veröffentlichen, fügt Visual Studio dem Projekt " *app. Manifest* " hinzu und fügt diese Option hinzu.

- Verwenden Sie kein Manifest. Erstellen Sie die Anwendung ohne ein Manifest.

   Diese Vorgehensweise wird auch als *Virtualisierung*bezeichnet. Verwenden Sie diese Option, um die Kompatibilität mit vorhandenen Anwendungen früherer Versionen von Visual Studio zu verwenden.

  Die neuen Eigenschaften sind auf der Seite **Anwendung** des Projekt-Designers (nur für Visual c#-Projekte) und im MSBuild-Projektdatei Format verfügbar.

  Die Methode zum Konfigurieren der Generierung von UAC-Manifesten in der Visual Studio-IDE unterscheidet sich je nach Projekttyp (Visual c# oder Visual Basic).

  * Weitere Informationen zum Konfigurieren von Visual c#-Projekten für die Generierung von Manifesten finden Sie unter [Seite "Anwendung", Projekt-Designer (c#)](../ide/reference/application-page-project-designer-csharp.md).

  * Weitere Informationen zum Konfigurieren von Visual Basic Projekten für die Generierung von Manifesten finden Sie unter [Seite "Anwendung", Projekt-Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).

## <a name="see-also"></a>Weitere Informationen
- [ClickOnce-Sicherheit und-Bereitstellung](../deployment/clickonce-security-and-deployment.md)
- [Benutzerberechtigungen und Visual Studio](/previous-versions/ms165100(v=vs.100))
- [Seite „Anwendung“, Projekt-Designer (C#)](../ide/reference/application-page-project-designer-csharp.md)
- [Seite „Anwendung“, Projekt-Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)