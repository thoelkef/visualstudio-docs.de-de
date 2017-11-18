---
title: Projekttypen erstellen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f7c0bba9b80e4e874f222ce00834f44a2d93e3e7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="creating-project-types"></a>Erstellen von Projekttypen
Sie können erweitern [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] durch einen neuen Projekttyp erstellen. Um einen neuen Projekttyp erstellen möchten, müssen Sie sich mit mehreren Konzepten vertraut, und führen eine Reihe von Schritten. Die folgenden Themen enthalten eine Übersicht über Projekttypen erstellen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Entwurfsentscheidungen bei Projekttypen](../../extensibility/internals/project-type-design-decisions.md)  
 Erläutert das Element, Datei projektdauerhaftigkeit und Verpflichtung Mechanic Designentscheidungen, die vorgenommen werden, bevor Sie einen neuen Projekttyp erstellen muss.  
  
 [Prüfliste: Erstellen neuer Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)  
 Bietet eine Übersicht über die Schritte, die Sie befolgen müssen, um einen neuen Projekttyp zu erstellen, der Programmieraufgaben als Code bearbeiten und kompilieren, erstellen, Debuggen und Bereitstellen von Anwendungen in Ihrem Projekt unterstützt.  
  
 [Erstellen von Projektinstanzen mithilfe von Projektfactorys](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 Enthält Informationen zum Bereitstellen und verwenden Sie eine Projekt Factory zum Erstellen von Instanzen eines neuen Projekts.  
  
 [Registrieren eines Projekttyps](../../extensibility/internals/registering-a-project-type.md)  
 Enthält Codebeispiele, die von Anweisungen aus der Registrierung, die Standardpfade und Daten und einer Tabelle bereitstellen, die Einträge aus dem Registrierungsskript "for each-Anweisung enthalten.  
  
 [Projektpersistenz](../../extensibility/internals/project-persistence.md)  
 Erläutert die Verwendung von `IPersistFileFormat` Datei- und nicht-Datei-basiertes Projektobjekte beibehalten werden.  
  
 [Verwenden von MSBuild](../../extensibility/internals/using-msbuild.md)  
 Beschreibt die Verwendung des Projekttyps die [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] erstellen Modul zum Erstellen von Benutzern zu ermöglichen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] und in der Befehlszeile.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Unterstützen von Tools zum Durchsuchen von Symbolen](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Erläutert die Architektur des Codes Tools wie z. B. Anzeigen der **Objektkatalog** und **Klassenansicht** Fenster. Beschreibt die Schnittstellen und Methoden, mit dem Objektbrowser in einem VSPackage implementiert werden.  
  
 [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 Erläutert die Bedeutung, die Projekte spielen bei der Bestimmung, welche-Editor verwendet wird, wenn ein Projektelement geöffnet wird und wie Projektressourcen bearbeitet werden können.  
  
 [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 Zeigt, wie Ihr VSPackage über eigene eindeutige Identität gewähren und Ihre VSPackage-DLLs und andere Informationen in einem Windows Installer-Paket Wrappen von (. MSI-Datei) für die Bereitstellung für Ihre Kunden.  
  
 [Hierarchien in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 Beschreibt, wie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Ansichten und Adressen Hierarchien.  
  
 [VSPackages](../../extensibility/internals/vspackages.md)  
 Bietet eine Übersicht über einem VSPackage, eine installierbare COM-Objekt, das erweitert die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Umgebung und erläutert, wie ein eigene VSPackage implementiert.  
  
 [Projekttypen](../../extensibility/internals/project-types.md)  
 Erläutert, wie Projekte verwenden, um Code zu ändern, kompilieren und erstellen Sie Code, und Code ausführen und Debuggen, und enthält Links zu ausführlichen Themen zur Vorgehensweise beim Erstellen von Projekttypen zur Verfügung.