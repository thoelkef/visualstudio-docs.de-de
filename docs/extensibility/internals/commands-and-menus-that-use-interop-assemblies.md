---
title: Befehle und Menüs, die Interop-Assemblys verwenden | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a1d87d761d27e9b77034eb5c36a71b4b5283de59
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53831062"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Befehle und Menüs, die Interop-Assemblys verwenden.
Eine VSPackage, die Menü-und Symbolleistenbefehle implementiert werden, mithilfe von Interop-Assemblys muss Schritte ausführen:  
  
- Informieren Sie die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (IDE) über die unterstützten Befehle und gibt an, ob sie derzeit aktiviert sind.  
  
- Beachten Sie die Regeln, (Vertrag) für die Behandlung von Befehlen.  
  
- Befehlsbehandlung explizit implementieren, indem Sie entweder die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> oder <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Schnittstelle.  
  
  Im folgende Abschnitt wird beschrieben, wie Sie diese Aufgaben durchführen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Bestimmen des Befehlsstatus mithilfe von Interop-Assemblys](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 Beschreibt, wie eine VSPackage für die IDE benachrichtigt dazu, welche Befehle sie unterstützt und gibt an, ob sie derzeit aktiviert sind.  
  
 [Befehlsverträge in Interop-Assemblys](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 Stellt eine Definition des Vertrags einfachen Befehl, die von allen VSPackages Implementieren von Befehlen, die mithilfe von Interop-Assemblys verwendet.
  
 [Befehlsimplementierung](../../extensibility/internals/command-implementation.md)  
 Bietet einen Überblick darüber, wie eine VSPackage einen Befehl implementiert.  
  
 [Registrieren der Befehlshandler von Interop-assembly](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 Beschreibt die Registrierungseinträge erforderlich, um der IDE benachrichtigt, dass eine VSPackage einen Befehlshandler bereitstellt.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Befehlsverfügbarkeit](../../extensibility/internals/command-availability.md)  
 Beschreibt die Kriterien, die von der IDE verwendet werden, um zu bestimmen, welche VSPackage-Befehle verfügbar sind und welches Objekt sie verarbeitet.  
  
 [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Enthält Details dazu, wie Sie eine Benutzeroberfläche erstellen, verwendet [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Befehl unterstützen.  
  
 [Befehlsrouting in VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)  
 Eine Übersicht über den Prozess verwendet, um ein Objekt mit den richtigen befehlsanforderung verknüpfen.