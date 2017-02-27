---
title: "Ausw&#228;hlen zwischen freigegebenen und versioniert VSPackages | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SxS"
  - "Side-by-Side installation"
  - "Side-by-Side-Installation [Visual Studio SDK]"
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# Ausw&#228;hlen zwischen freigegebenen und versioniert VSPackages
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Verschiedene Versionen von Visual Studio können auf dem gleichen Computer verwendet werden. VSPackages kann eine beliebige Kombination von unterstützen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Versionen.  
  
 Sie können die Seite\-an\-Seite\-Installationen von VSPackages über zwei Strategien, die gemeinsame Strategie oder die Strategie mit Versionsangabe. Beide gerecht zu werden, das Vorhandensein mehrerer Versionen von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und die zugehörigen Versionen der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 Ein VSPackage ist in der freigegebenen Strategie für die Verwendung in mehreren Versionen von registriert [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. In der Strategie mit Versionsangabe mehrere VSPackage\-DLLs installiert sind, eine für jede Version der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] die Sie unterstützen.  
  
## Freigegebene VSPackages  
 Mit einem freigegebenen VSPackage ist geeignet, wenn Sie das gleiche VSPackage in mehreren Versionen von verwenden [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Um eine freigegebene VSPackage implementieren zu können, müssen Sie die folgenden Schritte ausführen:  
  
-   Machen Sie Ihr VSPackage mit mehreren Versionen kompatibel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Zwei Möglichkeiten, dies sind also verfügbar:  
  
    -   Beschränken Sie das VSPackage nur die Funktionen der frühesten Version mit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] die Sie unterstützen.  
  
    -   Programmieren Sie Ihr VSPackage Anpassung an die Version der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] in der es ausgeführt wird. Klicken Sie dann, wenn Abfragen für neuere Dienste fehlschlagen, das VSPackage bieten andere Dienste, die in früheren Versionen von unterstützt werden [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Registrieren Sie Ihr VSPackage entsprechend. Weitere Informationen finden Sie unter [VSPackage\-Registrierung](../extensibility/internals/vspackage-registration.md) und [Managed VSPackage Registration](http://msdn.microsoft.com/de-de/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).  
  
-   Registrieren Sie die Erweiterungen entsprechend. Weitere Informationen finden Sie unter [Registrieren von Dateinamenerweiterungen für Seite\-an\-Seite\-Installationen](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   Erstellen Sie ein Installationsprogramm, das Ihr VSPackage für die entsprechenden Versionen der stellt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Weitere Informationen finden Sie unter [Installieren von VSPackages mit Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) und [Verwaltung von Komponenten](../extensibility/internals/component-management.md).  
  
-   Das Problem der Registrierung Konflikte zu beheben. Weitere Informationen finden Sie unter [VSPackage\-Registrierung](../extensibility/internals/vspackage-registration.md).  
  
-   Stellen Sie sicher, dass sowohl freigegebene als auch mit Versionsangabe verweiszählung, um sichere Installation und Deinstallation mehrerer Versionen ermöglichen berücksichtigen. Weitere Informationen finden Sie unter [Verwaltung von Komponenten](../extensibility/internals/component-management.md).  
  
## Mit Versionsangabe VSPackages  
 Unter der Versionsangabe VSPackage\-Strategie, die Sie erstellen ein VSPackage für jede Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] die Sie unterstützen. Dies ist sinnvoll, wenn Sie erwarten von späteren Versionen bereitgestellten Dienste nutzen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], da jede VSPackage weiterentwickelt werden kann, ohne Auswirkung auf die anderen. Dennoch kann die Versionsangabe Strategie zum Erstellen von mehreren Binärdateien aus einer einzigen Codebasis oder aus mehreren unabhängigen Codebasen Weitere Erstentwicklung als freigegebene Strategie gehören. Darüber hinaus zusätzliche Einrichtungsschritte möglicherweise erforderlichen müssen Sie entweder eine separate Installation für jede Version oder ein einzelnes Setup, das erkennt, die Versionen erstellen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] installiert werden und, die Ihr VSPackage unterstützt.  
  
## Binär\-Kompatibilität  
 Im Allgemeinen kann Binärkompatibilität systemeigenem Code VSPackages entwickelt, die mit früheren Versionen von Visual Studio in höheren Versionen von Visual Studio ausführen. Es gibt jedoch drei wichtige Ausnahmen:  
  
-   Wenn Ihr VSPackage stützt sich auf eine bestimmte Version der common Language Runtime, muss Sie ermitteln, welche Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] er ausgeführt wird.  
  
-   Ein VSPackage haben möglicherweise eine Abhängigkeit auf ein bestimmtes Feature von einem anderen VSPackage oder ein anderes Produkt. Folglich kann das VSPackage ausgeführt werden, bei dem nur die Abhängigkeit erfüllt ist.  
  
-   Ein VSPackage kann beeinträchtigt werden, durch ein Sicherheitsupdate in einem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Servicepack oder eine höhere Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. In diesen Fällen wird ein VSPackage mit einer früheren Version von entwickelt die [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] führen möglicherweise nicht in Versionen von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nachdem das Sicherheitsupdate angewendet wurde. Allerdings können neu erstellt das Paket mit der höheren Version und es auch in früheren Versionen ausführen.  
  
 Verwaltete VSPackages muss erstellt werden, mit einer Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] entsprechen die Zielversion des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Zusätzlich zur Planung für die binäre Kompatibilität für die VSPackage\-Binärdateien, sollte außerdem sollten Sie die Projektmappe und Projekt Dateiformate. Wenn Ihr VSPackage einen neuer Projekttyp erstellt, müssen Sie entscheiden, ob nur eine Version oder in mehreren Versionen von ausgeführt werden kann [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Weitere Informationen finden Sie unter [Aktualisieren von benutzerdefinierten Projekten](../misc/upgrading-custom-projects.md).  
  
## Siehe auch  
 [Installieren von VSPackages mit Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [Verwaltung von Komponenten](../extensibility/internals/component-management.md)