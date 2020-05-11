---
title: Befehlsverträge in Interop-Assemblys | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f20a4f479d62cd1b64c3b13ff6e1a949656a668
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709688"
---
# <a name="command-contracts-in-interop-assemblies"></a>Befehlsverträge in Interopassemblys
Der grundlegende Auftrag für <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> die Behandlung von Befehlen über die Schnittstelle besteht darin, dass die Umgebung die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode aufruft, um zu bestimmen, ob der Befehl unterstützt wird, und, wenn er unterstützt wird, um seinen Status und Text zu bestimmen. Anschließend ruft die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Umgebung die Methode zum Ausführen des Befehls auf.

 Die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode wird für alle Befehle identisch behandelt. Die weitere Kommunikation, falls erforderlich (z. B. mit <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Dropdownlisten), wird durch Aufrufen der Methode mit entsprechenden Parametern verwaltet. Die Interpretation dieser Parameter hängt vom angegebenen Befehl ab.

 Wenn das Befehlsziel Werte im Ausgabeparameter zurückgibt, ist der Aufrufer immer für die Freigabe der zugewiesenen Ressourcen verantwortlich. Da es sich bei diesem Parameter um eine Variante handelt, werden durch das Löschen der Variante die Ressourcen frei.

 In Fällen, in denen Befehle innerhalb <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> eines Hierarchiefensters ausgeführt werden müssen, muss die Schnittstelle verwendet werden. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Schnittstelle hat einen ähnlichen <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> Vertrag <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>mit ähnlichen Methoden: und .

## <a name="see-also"></a>Weitere Informationen
- [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Befehlsrouting in VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)
- [Befehlsimplementierung](../../extensibility/internals/command-implementation.md)
