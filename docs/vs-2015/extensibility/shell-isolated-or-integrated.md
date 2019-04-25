---
title: Shell (Isolated oder Integrated) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell
- Visual Studio, Shell
- Shell [Visual Studio]
- Visual Studio shell, shell-based applications
- Shell [Visual Studio], shell-based applications
ms.assetid: c64a9bf0-9bf8-45c3-8fa2-306fa6cab66a
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 17da1ff036227b50e507fd564618c4f53cf430c3
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60116380"
---
# <a name="shell-isolated-or-integrated"></a>Shell (Isolated oder Integrated)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Ihre eigene Anwendung mit Visual Studio-basierten isolierten oder integrated-Modus erstellen. Im integrierten Modus stehen viele Visual Studio-Funktionen zusätzlich zu Ihrer Anwendung. Im isolierten Modus wählen Sie einen Teil der Visual Studio-Features, die Sie zusammen mit Ihrer eigenen Extension verteilen möchten.  
  
## <a name="integrated-mode"></a>Im integrierten Modus  
 Im integrierter Modus kann Ihre Benutzer Visual Studio-Standardfunktionen sowie die benutzerdefinierten Tools zu verwenden. Die integrierte Shell dient in erster Linie für das Hosten von Programmiersprachen und Tools zur Softwareentwicklung.  
  
 Benutzerdefinierte Tools, die in der integrierten Shell, automatisch integriert sind Zusammenführen mit der eine andere Edition von Visual Studio, die auf dem gleichen Computer installiert ist. Sie können eine verteilbare Version der Visual Studio integrierte Shell bereitstellen, wenn Visual Studio nicht bereits installiert ist.  
  
 Die verteilbare Version der Visual Studio integrated Shell umfasst keine Programmiersprachen und die Funktionen, die jeweiligen Projektsysteme zu unterstützen.  
  
> [!NOTE]
>  Die integrierte Visual Studio-Shell-Modus kann zusammen mit allen Editionen von Visual Studio mit Ausnahme der Express-Editionen installiert werden.  
  
 Weitere Informationen finden Sie unter [Visual Studio Shell (integriert)](../extensibility/visual-studio-shell-integrated.md).  
  
## <a name="isolated-mode"></a>Isolationsmodus  
 Isolierte Modus können Sie benutzerdefinierte Tools erstellen, die Seite-an-Seite ausgeführt werden. mit anderen Versionen von Visual Studio. Es dient in erster Linie für Tools, die Visual Studio-Diensten ohne je nach den standardmäßigen Visual Studio-Features zugreifen können. Sie können die Darstellung von basiert auf der Visual Studio isolierte Shell-Anwendungen anpassen. Sie können ganz einfach deaktivieren Sie die Features und Menü Befehlsgruppen, die Sie nicht, angezeigt werden zusammen mit der Anwendung möchten.  
  
 Weitere Informationen finden Sie unter [Visual Studio Isolated Shell](../extensibility/visual-studio-isolated-shell.md).  
  
## <a name="distributing-your-integrated-or-isolated-shell-application"></a>Verteilen Ihrer integrierten oder isolierte Shellanwendung  
 Um die integrierten oder isolierte shellanwendung verteilen, müssen Sie Ihre Anwendung, eine spezielle integriert oder isoliert-Shell redistributable und ein Installationsprogramm enthalten. Weitere Informationen zu Verteilung und Installation finden Sie unter [Verteilen von Isolated Shell-Anwendungen](../extensibility/distributing-isolated-shell-applications.md).  
  
> [!IMPORTANT]
>  Die [(Endbenutzer-Lizenzvertrag)](https://www.visualstudio.com/support/legal/mt171552) für Visual Studio integrated und isolated Shells Abschnitt enthält, die Datensammlung (**Abschnitt 3. Daten**).  Es wird beschrieben, die Nutzung der Kundendaten, die von Microsoft Benutzer, der entweder integriert oder isolierte Shell-Software gesammelt werden können, die Sie in Ihrer Anwendung zu erstellen. Weitere Informationen finden Sie unter [Microsoft Visual Studio-Produktfamilie – Datenschutzbestimmungen](https://www.visualstudio.com/dn948229).  
> 
>  Wenn Sie separate Nutzungsdaten aus Ihrer Kunden durch Ihre Anwendung erfassen, müssen Sie die entsprechenden Beachten Sie, dass für Benutzer Ihrer Anwendung der Gegenstand der Sammlung bereitstellen.  Wenn Sie entweder die isolated oder integrated Shell-Software als Teil Ihrer Anwendung entsprechend der Visual Studio Software Development Kit-Lizenz, verteilen, müssen Sie eine der folgenden einschließen:  
> 
> - der Endbenutzer-Lizenzvertrag als Teil Ihrer Anwendung-Lizenz  
>   - Ihre eigenen Endbenutzer-Lizenzvertrag, die Ihre Kunden zu den Bedingungen zustimmen, die Visual Studio schützen erfordert integriert oder isoliert Shell mindestens so viel wie die Microsoft-Endbenutzer-Lizenzbedingungen für die Shell-software  
  
## <a name="additional-resources"></a>Zusätzliche Ressourcen  
 Weitere Informationen zu den verteilbaren Paketen finden Sie unter den [Downloads zu Visual Studio-Erweiterbarkeit](http://go.microsoft.com/fwlink/?LinkID=119298) Website.  
  
## <a name="see-also"></a>Siehe auch  
 [Bereitstellen von Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md)
