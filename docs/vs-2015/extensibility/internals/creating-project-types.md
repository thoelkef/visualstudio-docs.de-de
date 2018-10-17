---
title: Erstellen von Projekttypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6b23e63d8bf04c859b156a23a04af8a91b2dd932
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49260246"
---
# <a name="creating-project-types"></a>Erstellen von Projekttypen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sie können die erweitern [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] durch einen neuen Projekttyp erstellen. Um einen neuen Projekttyp zu erstellen, müssen Sie einige Konzepte verstehen und eine Reihe von Schritten ausführen. Die folgenden Themen enthalten eine Übersicht über zum Erstellen von Projekttypen zur Verfügung.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Entwurfsentscheidungen bei Projekttypen](../../extensibility/internals/project-type-design-decisions.md)  
 Beschreibt, Element, Projekt-Datei-Persistenz und Engagement Mechanic entwurfsentscheidungen, die Sie vornehmen, bevor ein neuer Projekttyp erstellen.  
  
 [Prüfliste: Erstellen neuer Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)  
 Bietet eine Übersicht über die Schritte, die Sie befolgen müssen, um einen neuen Projekttyp zu erstellen, der Programmieraufgaben, die als Code bearbeiten und kompilieren, erstellen, Debuggen und Bereitstellen von Anwendungen in Ihrem Projekt unterstützt.  
  
 [Erstellen von Projektinstanzen mithilfe von Projektfactorys](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 Enthält Informationen zum Bereitstellen und verwenden zum Erstellen von Instanzen eines neuen Projekts eine Projektzuordnungsinstanz.  
  
 [Registrieren eines Projekttyps](../../extensibility/internals/registering-a-project-type.md)  
 Enthält Codebeispiele, die von Anweisungen aus der Registrierung, die Standardpfade und Daten und eine Tabelle bereitstellen, die Einträge aus dem Registrierungsskript "for each-Anweisung enthalten.  
  
 [Projektpersistenz](../../extensibility/internals/project-persistence.md)  
 Erläutert die Verwendung von `IPersistFileFormat` Datei- und nicht-Datei-basiertes Projektobjekte beibehalten werden.  
  
 [Verwenden von MSBuild](../../extensibility/internals/using-msbuild.md)  
 Beschreibt, wie Ihr Projekttyp die [!INCLUDE[vstecmsbuild](../../includes/vstecmsbuild-md.md)] -build-Engine, um Benutzern das Erstellen von ermöglichen [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] und in der Befehlszeile.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Unterstützen von Tools zum Durchsuchen von Symbolen](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Erläutert die Architektur des Code-Tools wie z. B. Anzeigen der **Objektkatalog** und **Klassenansicht** Fenster. Beschreibt die Schnittstellen und Methoden, mit dem Objektkatalog in ein VSPackage implementiert werden.  
  
 [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 Erläutert die Bedeutung von Projekten bei der bestimmen, welcher Editor verwendet wird, wenn ein Projektelement geöffnet wird und wie die Ressourcen des Projekts geändert werden können.  
  
 [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 Zeigt, wie Ihr VSPackage über eine eigene eindeutige Identität gewähren und wie die VSPackage-DLLs und andere Informationen in einer Windows Installer-Paket zu umschließen (. MSI-Datei) für die Bereitstellung für Ihre Kunden.  
  
 [Hierarchien in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 Beschreibt, wie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Ansichten und Adressen Hierarchien.  
  
 [VSPackages](../../extensibility/internals/vspackages.md)  
 Bietet einen Überblick über die ein VSPackage, ein installierbares COM-Objekt, das erweitert die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Umgebung und erläutert, wie Sie eigene VSPackages zu implementieren.  
  
 [Projekttypen](../../extensibility/internals/project-types.md)  
 Erläutert, wie Projekte, Code zu ändern, kompilieren und erstellen Sie Code, und Code ausführen und Debuggen, und enthält Links zu ausführlichen Themen zur Vorgehensweise: Erstellen von Projekttypen zur Verfügung.

