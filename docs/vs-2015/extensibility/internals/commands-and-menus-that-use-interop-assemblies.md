---
title: Befehle und Menüs, die Interop-Assemblys verwenden | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ad6b324953914df7103d0dec7371199e3cbbd937
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195052"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Befehle und Menüs, die Interop-Assemblys verwenden
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ein VSPackage, das Menü-und Symbolleisten Befehle mithilfe von Interop-Assemblys implementiert, muss:  
  
- Informieren [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Sie die integrierte Entwicklungsumgebung (Integrated Development Environment, IDE) über die unterstützten Befehle und ob Sie zurzeit aktiviert sind.  
  
- Befolgen Sie die Regeln (Vertrag) für die Verarbeitung von Befehlen.  
  
- Implementieren Sie die Befehls Verarbeitung explizit mithilfe der- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> oder- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Schnittstelle.  
  
  Im folgenden wird beschrieben, wie diese Aufgaben ausgeführt werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Bestimmen des Befehlsstatus mithilfe von Interop-Assemblys](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 Beschreibt, wie ein VSPackage der IDE mitteilt, welche Befehle unterstützt werden und ob Sie derzeit aktiviert sind.  
  
 [Befehlsverträge in Interop-Assemblys](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 Stellt eine Definition des grundlegenden Befehls Vertrags bereit, der von allen VSPackages zum Implementieren von Befehlen mithilfe von Interop-Assemblys  
  
 [Implementierung](../../extensibility/internals/command-implementation.md)  
 Bietet einen Überblick darüber, wie ein VSPackage einen Befehl implementiert.  
  
 [Registrieren der Befehlshandler von Interop-Assemblys](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 Beschreibt die Registrierungseinträge, die zum Benachrichtigen der IDE erforderlich sind, dass ein VSPackage einen Befehls Handler bereitstellt.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Verfügbarkeit](../../extensibility/internals/command-availability.md)  
 Beschreibt die Kriterien, die von der IDE verwendet werden, um zu bestimmen, welche VSPackage-Befehle verfügbar sind und welches Objekt Sie behandelt.  
  
 [Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Bietet ausführliche Informationen zum Erstellen einer Benutzeroberfläche, die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Befehls Unterstützung verwendet.  
  
 [Befehlsrouting in VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)  
 Eine Übersicht über den Prozess, der verwendet wird, um ein Objekt mit der richtigen Befehls Anforderung zu verknüpfen.
