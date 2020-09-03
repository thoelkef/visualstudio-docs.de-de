---
title: Auswählen zwischen freigegebenen und versionierten VSPackages | Microsoft-Dokumentation
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
ms.openlocfilehash: 289e506d3cd404bba9a3a63d97179b89a948d381
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "67821981"
---
# <a name="choosing-between-shared-and-versioned-vspackages"></a>Auswählen zwischen freigegebenen VSPackages und VSPackages mit Versionsangabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verschiedene Versionen von Visual Studio können auf demselben Computer gleichzeitig vorhanden sein. VSPackages können eine beliebige Kombination von Versionen unterstützen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
 Parallele Installationen von VSPackages können mithilfe von zwei Strategien, der gemeinsam genutzten Strategie oder der Strategie für die Versionsverwaltung aktiviert werden. Beide ermöglichen das vorhanden sein mehrerer Versionen von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] und der zugehörigen Versionen von [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .  
  
 In der freigegebenen Strategie wird ein VSPackage für die Verwendung in mehreren Versionen von registriert [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . In der versionierten Strategie werden mehrere VSPackage-DLLs installiert, eine für jede von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Ihnen unterstützte Version von.  
  
## <a name="shared-vspackages"></a>Freigegebene VSPackages  
 Die Verwendung eines freigegebenen VSPackages ist geeignet, wenn Sie das gleiche VSPackage in mehreren Versionen von verwenden [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Zum Implementieren eines freigegebenen VSPackage müssen Sie die folgenden Schritte ausführen:  
  
- Sorgen Sie dafür, dass das VSPackage mit mehreren Versionen von kompatibel ist [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Hierfür stehen zwei Möglichkeiten zur Verfügung:  
  
  - Beschränken Sie das VSPackage auf die Verwendung der Features der frühesten Version von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , die Sie unterstützen.  

  - Program mieren Sie das VSPackage, um sich an die Version von anzupassen, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in der es ausgeführt wird. Wenn Abfragen für neuere Dienste fehlschlagen, kann das VSPackage weitere Dienste anbieten, die in älteren Versionen von unterstützt werden [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
- Registrieren Sie das VSPackage entsprechend. Weitere Informationen finden Sie unter [VSPackage-Registrierung](../extensibility/internals/vspackage-registration.md) und [verwaltete VSPackage-Registrierung](https://msdn.microsoft.com/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).  
  
- Registrieren Sie Dateierweiterungen entsprechend. Weitere Informationen finden Sie unter [Registrieren von Dateinamen Erweiterungen für](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)parallele bereit Stellungen.  
  
- Erstellen Sie ein Installationsprogramm, das das VSPackage für die entsprechenden Versionen von bereitstellt [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Weitere Informationen finden Sie unter [Installieren von VSPackages mit Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) und [Komponenten Verwaltung](../extensibility/internals/component-management.md).  
  
- Beheben Sie das Problem von Registrierungs Kollisionen. Weitere Informationen finden Sie unter [VSPackage-Registrierung](../extensibility/internals/vspackage-registration.md).  
  
- Stellen Sie sicher, dass sowohl freigegebene als auch Dateien mit Versions Angabe die Verweis Zählung beachten, um eine sichere Installation und Entfernung mehrerer Versionen zu ermöglichen Weitere Informationen finden Sie unter [Komponenten Verwaltung](../extensibility/internals/component-management.md).  
  
## <a name="versioned-vspackages"></a>Versionierte VSPackages  
 Unter der VSPackage-Strategie mit Versions Angabe erstellen Sie ein VSPackage für jede von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Ihnen unterstützte Version von. Dies ist sinnvoll, wenn Sie davon ausgehen, dass die von höheren Versionen von bereitgestellten Dienste genutzt [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] werden, da sich jedes VSPackage weiterentwickeln kann, ohne die anderen zu beeinflussen. Dennoch kann es bei der Strategie, mit der Sie mehrere Binärdateien erstellen, entweder aus einer einzelnen Codebasis oder aus mehreren unabhängigen Codebasen, eine größere anfängliche Entwicklung als bei der freigegebenen Strategie bedeuten. Außerdem sind möglicherweise zusätzliche Installationsschritte erforderlich, da Sie entweder ein separates Setup für jede Version oder eine einzelne Installation erstellen müssen, mit der die Versionen von erkannt werden, die von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Ihrem VSPackage unterstützt werden.  
  
## <a name="binary-compatibility"></a>Binäre Kompatibilität  
 Im allgemeinen ermöglicht die binäre Kompatibilität das Ausführen von VSPackages mit System eigenem Code, die mit früheren Versionen von Visual Studio entwickelt wurden, in neueren Versionen von Visual Studio. Es gibt jedoch drei wichtige Ausnahmen:  
  
- Wenn das VSPackage von einer bestimmten Version des Common Language Runtime abhängig ist, muss festgelegt werden, in welcher Version von das VSPackage [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ausgeführt wird.  
  
- Ein VSPackage kann eine Abhängigkeit von einer bestimmten Funktion eines anderen VSPackages oder eines anderen Produkts aufweisen. Folglich kann das VSPackage nur ausgeführt werden, wenn die Abhängigkeit erfüllt ist.  
  
- Ein VSPackage ist möglicherweise von einer Sicherheitskorrektur in einem [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Service Pack oder einer neueren Version von betroffen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . In diesen Fällen wird ein VSPackage, das mit einer früheren Version von entwickelt [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] wurde, möglicherweise nicht in Versionen von ausgeführt, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nachdem die Sicherheitskorrektur angewendet wurde. Sie können das Paket jedoch mit der neueren Version neu erstellen und auch in früheren Versionen ausführen.  
  
  Verwaltete VSPackages müssen mit einer Version von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] und der erstellt werden [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] , die der Zielversion von entsprechen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
  Neben der Planung der Binärkompatibilität für Ihre VSPackage-Binärdateien sollten Sie auch die Lösungs-und Projektdatei Formate berücksichtigen. Wenn das VSPackage einen neuen Projekttyp erstellt, müssen Sie entscheiden, ob es in nur einer Version oder in mehreren Versionen von ausgeführt werden kann [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Weitere Informationen finden Sie unter [Aktualisieren von benutzerdefinierten Projekten](../misc/upgrading-custom-projects.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Installieren von VSPackages mit Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [Verwaltung von Komponenten](../extensibility/internals/component-management.md)
