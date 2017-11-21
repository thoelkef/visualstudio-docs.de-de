---
title: Shell (isoliert oder integriert) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell
- Visual Studio, Shell
- Shell [Visual Studio]
- Visual Studio shell, shell-based applications
- Shell [Visual Studio], shell-based applications
ms.assetid: c64a9bf0-9bf8-45c3-8fa2-306fa6cab66a
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 92462699141f9d0a1af2d9eb461caadf4ee467ef
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="shell-isolated-or-integrated"></a>Shell (isoliert oder integriert)
Sie können eigene Visual Studio-basierten Anwendung im integrierten oder im isolierten Modus erstellen. Im integrierten Modus stehen viele Visual Studio-Funktionen zusätzlich zu Ihrer Anwendung. Im isolierten Modus wählen Sie eine Teilmenge von Visual Studio-Funktionen, die Sie zusammen mit Ihren eigenen Erweiterung verteilen möchten.  
  
## <a name="integrated-mode"></a>Im integrierten Modus  
 Im integrierter Modus ermöglicht Benutzern mithilfe von Visual Studio-Standardfunktionen sowie die benutzerdefinierten Tools. Die integrierte Shell dient in erster Linie zum Hosten von Programmiersprachen und Software Development Tools.  
  
 Benutzerdefinierte Tools, die auf die integrierte Shell, automatisch integriert sind Zusammenführen mit eine andere Edition von Visual Studio, die auf demselben Computer installiert ist. Sie können eine verteilbare Version der Visual Studio integrierten Shell bereitstellen, wenn Visual Studio nicht bereits installiert ist.  
  
 Die verteilbare Version von Visual Studio integrierte Shell enthält keine Programmiersprachen und die Funktionen, die jeweiligen Projektsysteme unterstützen.  
  
> [!NOTE]
>  Die integrierte Visual Studio-Shell-Modus kann zusammen mit allen Editionen von Visual Studio mit Ausnahme der Express-Editionen installiert werden.  
  
 Weitere Informationen finden Sie unter [Visual Studio Shell (integrierter Modus)](visual-studio-shell-integrated.md).  
  
## <a name="isolated-mode"></a>Isolierten Modus  
 Isolierte Modus können Sie benutzerdefinierte Tools erstellen, die Seite-an-Seite ausführen mit anderen Versionen von Visual Studio. Es dient in erster Linie für Tools, die Visual Studio-Dienste ohne abhängig von der standardmäßigen Visual Studio-Funktionen zugreifen können. Sie können die Darstellung von Anwendungen, die auf die Visual Studio isolated Shell anpassen. Sie können problemlos aktivieren, deaktivieren Sie die Funktionen und die im Menü Befehlsgruppen, die Sie nicht, die angezeigt werden zusammen mit der Anwendung möchten.  
  
 Weitere Informationen finden Sie unter [Visual Studio Isolated Shell](visual-studio-isolated-shell.md).  
  
## <a name="distributing-your-integrated-or-isolated-shell-application"></a>Verteilen der Shellanwendung integriert oder isolierte  
 Um die integrierte oder isolierte Shell-Anwendung verteilen, müssen Sie die Anwendung, eine besondere integrierte oder isolierte Shell, die verteilbare und kein Installationsprogramm enthalten. Weitere Informationen zur Verteilung und Installation finden Sie unter [isolierten Shell-Anwendungen Verteilen von](distributing-isolated-shell-applications.md).  
  
> [!IMPORTANT]
>  Die [Endbenutzer-Lizenzvertrag (EULA)](https://www.visualstudio.com/en-us/support/legal/mt171552) für Visual Studio integriert und isoliert enthält Shells einen Abschnitt für die Datensammlung (**Abschnitt 3. Daten**).  Es wird beschrieben, die Nutzungsdaten für Kunden, die von Microsoft Benutzer, der entweder integriert oder isolierte Shell Software gesammelt werden können, die Sie in Ihrer Anwendung zu erstellen. Weitere Informationen finden Sie unter [Microsoft Visual Studio Produktfamilie – Datenschutzbestimmungen](https://www.visualstudio.com/en-us/dn948229).  
>   
>  Wenn separate Nutzungsdaten aus Ihrer Kunden durch die Anwendung gesammelt, müssen Sie entsprechende Mitteilung bereitstellen, für Benutzer der Anwendung von was Sie erfassen.  Wenn Sie die isolierten oder integrierte Shell-Software als Teil Ihrer Anwendung entsprechend der Visual Studio-Software Development Kit-Lizenz verteilen, müssen Sie eine der folgenden einschließen:  
>   
>  -   die Endbenutzer-Lizenzvertrag als Teil Ihrer Anwendung-Lizenz  
> -   Ihre eigenen Endbenutzer-Lizenzvertrag, die Ihre Kunden zustimmen, die Visual Studio schützen erfordert integriert oder isolierte Shell mindestens so viel wie den Microsoft-Endbenutzer-Lizenzbedingungen für die Shell-software  
  
## <a name="additional-resources"></a>Zusätzliche Ressourcen  
 Weitere Informationen zu verteilbare Pakete, finden Sie unter der [Visual Studio-Erweiterbarkeit Downloads](http://go.microsoft.com/fwlink/?LinkID=119298) Website.  
  
## <a name="see-also"></a>Siehe auch  
 [Bereitstellen von Visual Studio-Erweiterungen](../shipping-visual-studio-extensions.md)