---
title: Auswählen zwischen freigegebenen und mit versionsverwaltung durch das VSPackages | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 49b5e5b7c36b09e08932fcb414478849a12a7c7b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58946440"
---
# <a name="choosing-between-shared-and-versioned-vspackages"></a>Auswählen zwischen freigegebenen VSPackages und VSPackages mit Versionsangabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verschiedene Versionen von Visual Studio können auf demselben Computer gleichzeitig vorhanden sein. VSPackages kann eine beliebige Kombination von unterstützen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Versionen.  
  
 Sie können die Seite-an-Seite-Installationen von VSPackages durch eine von zwei Strategien, die gemeinsam genutzten Strategie oder die Strategie mit versionsverwaltung durch das aktivieren. Sowohl das Vorhandensein mehrerer Versionen von aufzunehmen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] und die zugehörigen Versionen der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
 In der freigegebenen Strategie ist registriert ein VSPackage für die Verwendung in mehreren Versionen von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Bei der Strategie mit versionsverwaltung durch das mehrere VSPackage-DLLs installiert sind, eine für jede Version von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , die Sie unterstützen.  
  
## <a name="shared-vspackages"></a>Freigegebenen VSPackages  
 Mit einem freigegebenen VSPackage ist geeignet, bei der Verwendung der gleichen VSPackages in mehreren Versionen von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Um einen freigegebenen VSPackages zu implementieren, müssen Sie die folgenden Schritte ausführen:  
  
-   Machen Sie Ihr VSPackage mit mehreren Versionen kompatibel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Es sind also zwei Möglichkeiten, dies verfügbar:  
  
    -   Beschränken Sie Ihr VSPackage mit der nur die Funktionen der frühesten Version des [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , die Sie unterstützen.  
  
    -   Ihr VSPackage Programmieren zur Anpassung an die Version des [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in dem er ausgeführt wird. Klicken Sie dann, wenn Abfragen für neuere Dienste ein Fehler auftritt, das VSPackage bieten andere Dienste, die in früheren Versionen von Microsoft Intune [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
-   Registrieren Sie Ihr VSPackage entsprechend an. Weitere Informationen finden Sie unter [VSPackage-Registrierung](../extensibility/internals/vspackage-registration.md) und [verwalteten VSPackage-Registrierung](http://msdn.microsoft.com/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).  
  
-   Registrieren Sie die Dateierweiterungen entsprechend. Weitere Informationen finden Sie unter [Registrieren von Dateierweiterungen für Seite-an-Seite Bereitstellungen](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   Erstellen Sie ein Installationsprogramm, das das VSPackage für die richtigen Versionen der stellt [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Weitere Informationen finden Sie unter [Installieren von VSPackages mit Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) und [Komponentenverwaltung](../extensibility/internals/component-management.md).  
  
-   Das Problem der Registrierung Konflikte zu beheben. Weitere Informationen finden Sie unter [VSPackage-Registrierung](../extensibility/internals/vspackage-registration.md).  
  
-   Stellen Sie sicher, dass sowohl freigegebene als auch mit versionsverwaltung durch das sichere Installation und Deinstallation von mehreren Versionen ermöglichen zählen von Verweisen berücksichtigt. Weitere Informationen finden Sie unter [Komponentenverwaltung](../extensibility/internals/component-management.md).  
  
## <a name="versioned-vspackages"></a>Mit versionsverwaltung durch das VSPackages  
 Unter der mit versionsverwaltung durch das VSPackage-Strategie, die Sie erstellen ein VSPackage für jede Version von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , die Sie unterstützen. Dadurch eignet sich, wenn Sie erwarten, dass spätere Versionen der bereitgestellten Dienste nutzen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], da jedes VSPackage entwickeln kann, ohne Auswirkung auf die anderen. Die Versionsangabe Strategie zum mehrere Binärdateien erstellen, aus einer einzelnen Codebasis oder von mehreren und unabhängige Codebasen, möglicherweise dennoch weitere Entwicklung als Strategie für die freigegebene gelten. Darüber hinaus zusätzliche Einrichtung kann erforderlich sein, da Sie erstellen müssen, entweder eine separate Installation für jede Version oder ein einmaliges Setup, das erkennt, die Versionen der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , installiert und, die das VSPackage unterstützt.  
  
## <a name="binary-compatibility"></a>Binäre Kompatibilität  
 Im Allgemeinen ermöglicht die binäre Kompatibilität systemeigenem Code VSPackages, die mit früheren Versionen von Visual Studio zum Ausführen in höheren Versionen von Visual Studio entwickelt wurden. Es gibt jedoch drei wichtige Ausnahmen:  
  
- Wenn das VSPackage auf eine bestimmte Version der common Language Runtime verwendet, müssen sie bestimmen, in welcher Version von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] er ausgeführt wird.  
  
- Eine VSPackage kann eine bestimmte Funktion von einem anderen VSPackage oder ein anderes Produkt eine Abhängigkeit aufweisen. Daher kann das VSPackage ausgeführt werden, in dem nur die Abhängigkeit erfüllt wird.  
  
- Eine VSPackage kann beeinflusst werden, durch ein Sicherheitsupdate in einer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Servicepack oder eine höhere Version von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. In diesen Fällen an, die für eine VSPackage mit einer früheren Version von entwickelt wurden die [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] möglicherweise nicht ausgeführt werden, in Versionen von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nachdem die Lösung für Sicherheit angewendet wurde. Sie können allerdings erstellen Sie das Paket mit der höheren Version neu und ihn auch in früheren Versionen ausführen.  
  
  Verwaltete VSPackages muss erstellt werden, mit einer Version von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] und [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] , entsprechen die Zielversion des [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
  Zusätzlich zur Planung für die binäre Kompatibilität für Ihr VSPackage-Binärdateien, sollten außerdem Lösung und Projekt-Dateiformate. Wenn Ihr VSPackage einen neuer Projekttyp erstellt, müssen Sie entscheiden, ob die Ausführung kann nur eine Version oder in mehreren Versionen von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Weitere Informationen finden Sie unter [Aktualisieren von benutzerdefinierten Projekten](../misc/upgrading-custom-projects.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Installieren von VSPackages mit Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [Verwaltung von Komponenten](../extensibility/internals/component-management.md)
