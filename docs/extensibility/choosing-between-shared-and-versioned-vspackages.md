---
title: "Auswählen zwischen freigegebenen und mit Versionsangabe VSPackages | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9442d6685d27a9270c1e71e3a79e9f810b6f40f0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="choosing-between-shared-and-versioned-vspackages"></a>Auswählen zwischen freigegebenen und mit Versionsangabe VSPackages
Verschiedene Versionen von Visual Studio können auf demselben Computer installiert werden. VSPackages kann eine beliebige Kombination von unterstützen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Versionen.  
  
 Sie können die Seite-an-Seite-Installationen von VSPackages über zwei Strategien, die freigegebene Strategie oder die Strategie mit versionsverwaltung durch das aktivieren. Sowohl das Vorhandensein mehrerer Versionen aufzunehmen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und die zugehörigen Versionen der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 Ein VSPackage ist in der freigegebenen Strategie für die Verwendung in mehreren Versionen von registriert [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. In der Strategie mit Versionsangabe mehrere VSPackage-DLLs installiert sind, eine für jede Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , die Sie unterstützen.  
  
## <a name="shared-vspackages"></a>Freigegebene VSPackages  
 Verwenden einer freigegebenen VSPackages ist geeignet, bei der Verwendung der gleichen VSPackages in mehreren Versionen von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Um eine freigegebene VSPackage implementieren zu können, müssen Sie die folgenden Schritte ausführen:  
  
-   Stellen Sie das VSPackage kompatibel mit mehreren Versionen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Zwei Möglichkeiten, dies sind daher verfügbar:  
  
    -   Beschränken Sie Ihre VSPackage, um nur die Funktionen der frühesten Version mit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , die Sie unterstützen.  
  
    -   Ihr VSPackage Programmieren Anpassung an die Version des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] in dem er ausgeführt wird. Klicken Sie dann, wenn Abfragen für neuere Services ein Fehler auf, das VSPackage bieten andere Dienste, die in früheren Versionen von unterstützt werden [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Registrieren Sie Ihr VSPackage entsprechend an. Weitere Informationen finden Sie unter [VSPackage Registrierung](../extensibility/internals/vspackage-registration.md) und [verwalteten VSPackage Registrierung](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).  
  
-   Registrieren Sie Dateierweiterungen entsprechend an. Weitere Informationen finden Sie unter [registrieren Dateinamenerweiterungen für Seite-an-Seite-Bereitstellungen](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   Erstellen Sie ein Installationsprogramm, das das VSPackage für die entsprechenden Versionen der stellt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Weitere Informationen finden Sie unter [Installieren von VSPackages mit Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) und [Komponente Management](../extensibility/internals/component-management.md).  
  
-   Behandeln Sie das Problem der Registrierung Kollisionen. Weitere Informationen finden Sie unter [VSPackage Registrierung](../extensibility/internals/vspackage-registration.md).  
  
-   Stellen Sie sicher, dass sowohl freigegebene als auch mit Versionsangabe Dateien, verweiszählung berücksichtigen, um sichere Installation und Deinstallation von mehreren Versionen zu ermöglichen. Weitere Informationen finden Sie unter [Komponente Management](../extensibility/internals/component-management.md).  
  
## <a name="versioned-vspackages"></a>Mit Versionsangabe VSPackages  
 Rahmen mit versionsverwaltung durch das VSPackage-Strategie, erstellen Sie ein VSPackage für jede Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , die Sie unterstützen. Dies ist sinnvoll, wenn Sie erwarten, dass von späteren Versionen bereitgestellten Dienste nutzen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], da jedes VSPackage ohne Auswirkung auf die anderen weiterentwickeln kann. Die Strategie die mit versionsverwaltung durch das Erstellen mehrerer Binärdateien von einer einzelnen Codebasis oder mehrere unabhängige Codebasen möglicherweise trotzdem weitere Erstentwicklung als freigegebene Strategie gelten. Darüber hinaus zusätzliche Einrichtung möglicherweise erforderlich, da Sie erstellen müssen, entweder eine separate Installation für jede Version oder ein einzelnes Setup, das erkennt die Versionen der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , installiert sind und, die das VSPackage unterstützt.  
  
## <a name="binary-compatibility"></a>Binäre Kompatibilität  
 Im Allgemeinen kann Binärkompatibilität systemeigenem Code VSPackages, die mit früheren Versionen von Visual Studio ausführen in höheren Versionen von Visual Studio entwickelt wurde. Es gibt jedoch drei wichtige Ausnahmen:  
  
-   Wenn Ihr VSPackage basiert auf einer bestimmten Version der common Language Runtime, muss es bestimmen, welche Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ausgeführt wird.  
  
-   Eine VSPackage kann ein bestimmtes Feature von einem anderen VSPackage oder ein anderes Produkt eine Abhängigkeit aufweisen. Daher kann das VSPackage ausgeführt werden, in dem die Abhängigkeit erfüllt wird.  
  
-   Eine VSPackage beeinträchtigt werden könnte, durch eine Korrektur Sicherheit in einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Servicepack oder eine höhere Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. In diesen Fällen entwickelt eine VSPackage mit einer früheren Version von den [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] möglicherweise nicht ausgeführt werden, in Versionen von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nach dem Anwenden der Sicherheit Korrekturen. Sie können allerdings erstellen Sie das Paket mit der höheren Version neu und ihn auch in früheren Versionen ausführen.  
  
 Verwaltete VSPackages muss erstellt werden, mit einer Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] , entsprechen die Zielversion des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Zusätzlich zur Planung für die binäre Kompatibilität für die VSPackage-Binärdateien, sollte außerdem sollten Sie die Projektmappe und Projekt Dateiformate. Wenn Ihr VSPackage einen neuen Projekttyp erstellt, müssen Sie entscheiden, ob nur eine Version oder in mehreren Versionen von ausgeführt werden kann [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Weitere Informationen finden Sie unter [Upgrade benutzerdefinierte Projekte](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects).  
  
## <a name="see-also"></a>Siehe auch  
 [Installieren von VSPackages mit Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [Verwaltung von Komponenten](../extensibility/internals/component-management.md)