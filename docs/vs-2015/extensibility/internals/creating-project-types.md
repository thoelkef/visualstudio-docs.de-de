---
title: Erstellen von Projekttypen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bbe65d1615603e4dc7546dbfe3530093c62528e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155026"
---
# <a name="creating-project-types"></a>Erstellen von Projekttypen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sie können erweitern, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] indem Sie einen neuen Projekttyp erstellen. Um einen neuen Projekttyp zu erstellen, müssen Sie verschiedene Konzepte verstehen und eine Reihe von Schritten ausführen. Die folgenden Themen bieten eine Übersicht über das Erstellen von Projekttypen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Entwurfsentscheidungen bei Projekttypen](../../extensibility/internals/project-type-design-decisions.md)  
 Erläutert die Entwurfsentscheidungen für Elemente, Projektdateien und Verpflichtungen, die Sie vor dem Erstellen eines neuen Projekt Typs treffen müssen.  
  
 [Prüfliste: Erstellen neuer Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)  
 Bietet einen Überblick über die Schritte, die Sie ausführen müssen, um einen neuen Projekttyp zu erstellen, der Programmieraufgaben als Bearbeiten von Code und kompilieren, erstellen, Debuggen und Bereitstellen von Anwendungen in Ihrem Projekt unterstützt.  
  
 [Erstellen von Projektinstanzen mithilfe von Projektfactorys](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 Enthält Informationen zum Bereitstellen und Verwenden einer projektfactory zum Erstellen von Instanzen eines neuen Projekts.  
  
 [Registrieren eines Projekttyps](../../extensibility/internals/registering-a-project-type.md)  
 Bietet Codebeispiele für Anweisungen aus der Registrierung, die Standard Pfade und-Daten bereitstellen, sowie eine Tabelle, die Einträge aus dem Registrierungs Skript für jede Anweisung enthält.  
  
 [Projektpersistenz](../../extensibility/internals/project-persistence.md)  
 Erläutert die Verwendung von `IPersistFileFormat` zum Beibehalten von Datei-und nicht dateibasierten Projekt Objekten.  
  
 [Verwenden von MSBuild](../../extensibility/internals/using-msbuild.md)  
 Beschreibt, wie Ihr Projekttyp die [!INCLUDE[vstecmsbuild](../../includes/vstecmsbuild-md.md)] Build-Engine verwenden kann, um Benutzern das Erstellen aus [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] und in der Befehlszeile zu ermöglichen.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Unterstützen von Tools zum Durchsuchen von Symbolen](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Erläutert die Architektur von Tools zur Code Anzeige, wie z. b. das Fenster **Objektkatalog** und **Klassenansicht** . Beschreibt die Schnittstellen und Methoden, die zum Implementieren des Objekt Suchens in einem VSPackage verwendet werden.  
  
 [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 Erläutert die Bedeutung, die die Projekte spielen, um zu bestimmen, welcher Editor verwendet wird, wenn ein Projekt Element geöffnet wird und wie Projektressourcen bearbeitet werden können.  
  
 [Installieren von VSPackages mit Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 Zeigt, wie Sie Ihrem VSPackage eine eigene eindeutige Identität zuordnen und wie Sie Ihre VSPackage-DLLs und andere Informationen in einem Windows Installer Paket (. MSI-Datei) für die Bereitstellung für Ihre Kunden.  
  
 [Hierarchien in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 Beschreibt die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Hierarchien von Sichten und Adressen.  
  
 [VSPackages](../../extensibility/internals/vspackages.md)  
 Bietet einen Überblick über ein VSPackage, ein installier bares com-Objekt, das die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Umgebung erweitert und erläutert, wie Sie ein eigenes VSPackage implementieren.  
  
 [Projekttypen](../../extensibility/internals/project-types.md)  
 Erläutert die Verwendung von-Projekten zum Ändern von Code, kompilieren und Erstellen von Code sowie ausführen und Debuggen von Code und bietet Links zu detaillierten Themen zum Erstellen von Projekttypen.
