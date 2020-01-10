---
title: Hierarchien in Visual Studio | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 08005b69a1af16b07212cb29547875fad89e1d6a
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848940"
---
# <a name="hierarchies-in-visual-studio"></a>Hierarchien in Visual Studio
In der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wird ein Projekt als *Hierarchie*angezeigt. In der IDE ist eine Hierarchie eine Struktur von Knoten, in der jeder Knoten über einen Satz zugeordneter Eigenschaften verfügt. Eine *Projekt Hierarchie* ist ein Container, der die Elemente des Projekts, die Beziehungen der Elemente und die zugeordneten Eigenschaften und Befehle der Elemente enthält.

 In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]verwalten Sie Projekt Hierarchien mithilfe der Hierarchie Schnittstelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>-Schnittstelle leitet Befehle, die Sie von Projekt Elementen aufrufen, anstelle des Standard Befehls Handlers in das entsprechende Hierarchie Fenster um.

## <a name="project-hierarchies"></a>Projekt Hierarchien
 Jede Projekt Hierarchie enthält Elemente, die Sie anzeigen und bearbeiten können. Diese Elemente variieren abhängig vom Projekttyp. Ein Datenbankprojekt kann z. b. gespeicherte Prozeduren, Daten Bank Sichten und Datenbanktabellen enthalten. Ein Programmier Sprachprojekt hingegen enthält wahrscheinlich Quelldateien und Ressourcen Dateien für Bitmaps und Dialogfelder. Hierarchien können eingebettet werden, was Ihnen beim Erstellen einer Projekt Hierarchie zusätzliche Flexibilität bietet.

 Wenn Sie einen neuen Projekttyp erstellen, steuert der Projekttyp den gesamten Satz von Elementen, die darin bearbeitet werden können. Projekte können jedoch Elemente enthalten, für die Sie nicht über Bearbeitungs Unterstützung verfügen. Visuelle C++ Projekte können z. b. HTML-Dateien enthalten, obwohl C++ Visual keinen angepassten Editor für den HTML-Dateityp bereitstellt.

 Hierarchien verwalten die Persistenz der Elemente, die Sie enthalten. Die Implementierung der Hierarchie muss alle besonderen Eigenschaften steuern, die sich auf die Persistenz der Elemente in der Hierarchie auswirken. Wenn die Elemente z. b. Objekte in einem Repository anstelle von Dateien darstellen, muss die Hierarchie Implementierung die Persistenz dieser Objekte steuern. Die IDE leitet die Hierarchie so um, dass die Elemente in Übereinstimmung mit der Benutzereingabe gespeichert werden, aber die IDE steuert keine Aktionen, die zum Speichern dieser Elemente erforderlich sind. Stattdessen befindet sich das Projekt in der Kontrolle.

 Wenn ein Benutzer ein Element in einem Editor öffnet, wird die Hierarchie, die dieses Element steuert, ausgewählt und zur aktiven Hierarchie. Die ausgewählte Hierarchie bestimmt den Satz von Befehlen, die für das Element zur Verfügung stehen. Wenn Sie den Fokus des Benutzers auf diese Weise nachverfolgen, kann die Hierarchie den aktuellen Kontext des Benutzers widerspiegeln.

## <a name="see-also"></a>Siehe auch
- [Projekttypen](../../extensibility/internals/project-types.md)
- [Auswahl und Währung in der IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [VSSDK-Beispiele](https://github.com/Microsoft/VSSDK-Extensibility-Samples)
