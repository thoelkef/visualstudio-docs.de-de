---
title: "Shell (isoliert oder integriert) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio-shell"
  - "Visual Studio Shell"
  - "Shell [Visual Studio]"
  - "Visual Studio-Shell, Shell-basierten Anwendung"
  - "Shell-basierte-Shell [Visual Studio]"
ms.assetid: c64a9bf0-9bf8-45c3-8fa2-306fa6cab66a
caps.latest.revision: 25
caps.handback.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
---
# Shell (isoliert oder integriert)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können Ihre eigene Visual Studio\-basierte Anwendung im integrierten oder im isolierten Modus erstellen. Im integrierten Modus stehen viele Visual Studio\-Funktionen neben der Anwendung. Im isolierten Modus wählen Sie eine Teilmenge der Visual Studio\-Funktionen, die Sie zusammen mit Ihren eigenen Erweiterung verteilen möchten.  
  
## Im integrierten Modus  
 Im integrierter Modus ermöglicht den Benutzern standardmäßige Visual Studio\-Funktionen sowie die benutzerdefinierten Tools verwenden. Die integrierte Shell dient in erster Linie für das Hosten von Programmiersprachen und Tools zur Softwareentwicklung.  
  
 Benutzerdefinierte Tools, die auf die integrierte Shell, automatisch integriert sind Zusammenführen mit allen anderen Editionen von Visual Studio, die auf demselben Computer installiert ist. Sie können eine verteilbare Version von Visual Studio integrierte Shell bereitstellen, wenn Visual Studio nicht bereits installiert ist.  
  
 Die verteilbare Version von Visual Studio integrierte Shell enthält keine Programmiersprachen oder Funktionen, die zur Unterstützung der jeweiligen Projektsysteme.  
  
> [!NOTE]
>  Die integrierte Visual Studio\-Shell\-Modus kann zusammen mit allen Editionen von Visual Studio mit Ausnahme der Express\-Editionen installiert werden.  
  
 Weitere Informationen finden Sie unter [Visual Studio\-Shell \(integriert\)](../extensibility/visual-studio-shell-integrated.md).  
  
## Isolierten Modus  
 Isolierter Modus können Sie benutzerdefinierte Tools erstellen, die Side\-by\-Side\-Ausführung mit anderen Versionen von Visual Studio. Sie dient in erster Linie für Tools, die Visual Studio\-Dienste ohne abhängig von der standardmäßigen Visual Studio\-Funktionen zugreifen können. Sie können die Darstellung der bei Visual Studio isolated Shell anpassen. Sie können problemlos deaktivieren der Funktionen und der Befehl Menügruppen, die Sie nicht, werden zusammen mit Ihrer Anwendung möchten.  
  
 Weitere Informationen finden Sie unter [Visual Studio Shell Isolated](../extensibility/visual-studio-isolated-shell.md).  
  
## Bereitstellen der Shellanwendung integriert oder isolierte  
 Um die integrierte oder isolierte Shell\-Anwendung verteilen, müssen Sie die Anwendung, eine spezielle integrierte oder isoliert\-Shell redistributable und ein Installationsprogramm enthalten. Weitere Informationen zur Verteilung und Installation, finden Sie unter [Isolierte Shell anwendungsverteilung](../extensibility/distributing-isolated-shell-applications.md).  
  
> [!IMPORTANT]
>  Die [Endbenutzer\-Lizenzvertrag \(EULA\)](https://www.visualstudio.com/en-us/support/legal/mt171552) für Visual Studio integriert und isolierte Shells Abschnitt enthält, für die Datensammlung \(**Abschnitt 3. Data**\).  Es beschreibt die Nutzung der Kundendaten, die von Microsoft von der Software integriert oder isolierte Shell\-Benutzern erfasst werden können, die Sie in Ihre Anwendung integrieren. Weitere Informationen finden Sie unter [Microsoft Visual Studio Datenschutzbestimmungen\-Produktfamilie](https://www.visualstudio.com/en-us/dn948229).  
>   
>  Wenn Sie separate Daten Ihrer Kunden durch die Anwendung erfassen, müssen Sie entsprechende Mitteilung an Benutzer der Anwendung der Gegenstand der Sammlung angeben. Beim Verteilen von Software isoliert oder integrierte Shell als Teil der Anwendung gemäß der Lizenz für Visual Studio Software Development Kit, müssen Sie eine der folgenden einschließen:  
>   
>  -   der Endbenutzer\-Lizenzvertrag als Teil Ihrer Anwendung\-Lizenz  
> -   eigene EULA, die Ihre Kunden akzeptieren, die Visual Studio schützen muss integriert oder isolierte Shell mindestens genauso viel wie dem Microsoft\-Endbenutzer\-Lizenzvertrag für die Shell\-software  
  
## Zusätzliche Ressourcen  
 Weitere Informationen zu den verteilbaren Paketen, finden Sie unter der [Downloads zu Visual Studio\-Erweiterbarkeit](http://go.microsoft.com/fwlink/?LinkID=119298) Website.  
  
## Siehe auch  
 [Lieferung von Visual Studio\-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md)