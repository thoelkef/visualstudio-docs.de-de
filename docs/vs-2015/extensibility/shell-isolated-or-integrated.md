---
title: Shell (isoliert oder integriert) | Microsoft-Dokumentation
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
ms.openlocfilehash: aa346ebfe321e4672ea3fa71a4dcc872ebf22cda
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850230"
---
# <a name="shell-isolated-or-integrated"></a>Shell (isoliert oder integriert)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Ihre eigene, auf Visual Studio basierende Anwendung im integrierten oder isolierten Modus erstellen. Im integrierten Modus stehen viele Funktionen von Visual Studio über Ihre Anwendung hinaus zur Verfügung. Im isolierten Modus wählen Sie eine Teilmenge von Visual Studio-Funktionen aus, die Sie zusammen mit Ihrer eigenen Extension verteilen möchten.  
  
## <a name="integrated-mode"></a>Integrierter Modus  
 Der integrierte Modus ermöglicht es Ihren Benutzern, Visual Studio-Standardfunktionen zusammen mit Ihren benutzerdefinierten Tools zu verwenden. Die integrierte Shell dient hauptsächlich zum Hosting von Programmiersprachen und Software Entwicklungs Tools.  
  
 Benutzerdefinierte Tools, die auf der integrierten Shell erstellt werden, werden automatisch mit jeder anderen Edition von Visual Studio zusammengeführt, die auf dem gleichen Computer installiert ist. Wenn Visual Studio noch nicht installiert ist, können Sie eine verteilbare Version von Visual Studio Integrated Shell bereitstellen.  
  
 Die weitervertreibbare Version der Visual Studio-integrierten Shell umfasst keine Programmiersprachen und die Features, die ihre jeweiligen Projektsysteme unterstützen.  
  
> [!NOTE]
> Der integrierte Visual Studio Shell-Modus kann mit allen Editionen von Visual Studio installiert werden, mit Ausnahme der Express-Editionen.  
  
 Weitere Informationen finden Sie unter [Visual Studio Shell (integriert)](../extensibility/visual-studio-shell-integrated.md).  
  
## <a name="isolated-mode"></a>Isolierter Modus  
 Der isolierte Modus ermöglicht es Ihnen, benutzerdefinierte Tools zu erstellen, die parallel mit anderen Versionen von Visual Studio ausgeführt werden. Sie ist in erster Linie für Tools vorgesehen, die auf Visual Studio-Dienste zugreifen können, ohne dass alle Visual Studio-Standard Features in Abhängigkeit sind. Sie können die Darstellung von Anwendungen anpassen, die auf der isolierten Visual Studio-Shell basieren. Sie können die Features und Menübefehls Gruppen, die nicht in der Anwendung angezeigt werden sollen, mühelos deaktivieren.  
  
 Weitere Informationen finden Sie unter [isolierte Visual Studio-Shell](../extensibility/visual-studio-isolated-shell.md).  
  
## <a name="distributing-your-integrated-or-isolated-shell-application"></a>Verteilen der integrierten oder isolierten Shellanwendung  
 Um Ihre integrierte oder isolierte Shellanwendung zu verteilen, müssen Sie Ihre Anwendung, eine spezielle integrierte oder isolierte Shell-weitervertreibbare Komponente und ein Installationsprogramm einschließen. Weitere Informationen zur Verteilung und Installation finden Sie unter [verteilen isolierter Shellanwendungen](../extensibility/distributing-isolated-shell-applications.md).  
  
> [!IMPORTANT]
> Der [Endbenutzer-Lizenzvertrag (EULA)](https://www.visualstudio.com/support/legal/mt171552) für die integrierten und isolierten Shells von Visual Studio enthält einen Abschnitt zur Datensammlung (**Abschnitt 3). Daten**).  Es beschreibt die Kunden Verwendungs Daten, die von Microsoft von Benutzern der integrierten oder isolierten shellsoftware, die Sie in Ihrer Anwendung erstellen, gesammelt werden können. Weitere Informationen finden Sie unter [Datenschutzbestimmungen für Microsoft Visual Studio-Produktfamilie](https://www.visualstudio.com/dn948229).  
> 
> Wenn Sie von ihren Kunden getrennte Nutzungsdaten über Ihre Anwendung erfassen, müssen Sie die Benutzer Ihrer Anwendung entsprechend benachrichtigen.  Wenn Sie entweder die isolierte oder integrierte shellsoftware als Teil Ihrer Anwendung verteilen, müssen Sie gemäß der Lizenz für das Visual Studio Software Development Kit eine der folgenden Optionen einschließen:  
> 
> - der Endbenutzer-Lizenzvertrag als Teil ihrer Anwendungs Lizenz  
> - Ihre eigenen EULA, bei denen Ihre Kunden den Bedingungen zustimmen müssen, die die integrierte oder isolierte Shell von Visual Studio schützen, zumindest so weit wie die Microsoft-Endbenutzer-Lizenzbedingungen für die shellsoftware.  
  
## <a name="additional-resources"></a>Zusätzliche Ressourcen  
 Weitere Informationen zu verteilbaren Paketen finden Sie auf der Website [Visual Studio-Erweiterbarkeits Downloads](https://msdn.microsoft.com/vstudio/bb984878.aspx) .  
  
## <a name="see-also"></a>Siehe auch  
 [Bereitstellen von Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md)
