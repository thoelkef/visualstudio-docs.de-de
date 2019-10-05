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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68195052"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Befehle und Menüs, die Interop-Assemblys verwenden
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Eine VSPackage, die Menü-und Symbolleistenbefehle implementiert werden, mithilfe von Interop-Assemblys muss Schritte ausführen:  
  
- Informieren Sie die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrierte Entwicklungsumgebung (IDE) über die unterstützten Befehle und gibt an, ob sie derzeit aktiviert sind.  
  
- Beachten Sie die Regeln, (Vertrag) für die Behandlung von Befehlen.  
  
- Befehlsbehandlung explizit implementieren, indem Sie entweder die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> oder <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Schnittstelle.  
  
  Im folgenden wird beschrieben, wie Sie diese Aufgaben durchführen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Bestimmen des Befehlsstatus mithilfe von Interop-Assemblys](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 Beschreibt, wie eine VSPackage für die IDE benachrichtigt dazu, welche Befehle sie unterstützt und gibt an, ob sie derzeit aktiviert sind.  
  
 [Befehlsverträge in Interop-Assemblys](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 Stellt eine Definition des Vertrags einfachen Befehl ein, die allen VSPackages Implementieren von Befehlen, die mithilfe von Interopassemblys  
  
 [Implementation (Implementierung)](../../extensibility/internals/command-implementation.md)  
 Bietet einen Überblick darüber, wie eine VSPackage einen Befehl implementiert.  
  
 [Registrieren der Befehlshandler von Interop-Assemblys](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 Beschreibt die Registrierungseinträge erforderlich, um der IDE benachrichtigt, dass eine VSPackage einen Befehlshandler bereitstellt.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Verfügbarkeit](../../extensibility/internals/command-availability.md)  
 Beschreibt die Kriterien, die von der IDE verwendet werden, um zu bestimmen, welche VSPackage-Befehle verfügbar sind und welches Objekt sie verarbeitet.  
  
 [Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Enthält Details dazu, wie Sie eine Benutzeroberfläche erstellen, verwendet [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Befehl unterstützen.  
  
 [Befehlsrouting in VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)  
 Eine Übersicht über den Prozess verwendet, um ein Objekt mit den richtigen befehlsanforderung verknüpfen.
