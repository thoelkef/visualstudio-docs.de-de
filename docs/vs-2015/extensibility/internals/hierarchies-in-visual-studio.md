---
title: Hierarchien
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 22943d3049ff0e24d00c7c29750e7dcd0efaf846
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158359"
---
# <a name="hierarchies-in-visual-studio"></a>Hierarchien in Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]In der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) wird ein Projekt als *Hierarchie*angezeigt. In der IDE ist eine Hierarchie eine Struktur von Knoten, in der jeder Knoten über einen Satz zugeordneter Eigenschaften verfügt. Eine *Projekt Hierarchie* ist ein Container, der die Elemente des Projekts, die Beziehungen der Elemente und die zugeordneten Eigenschaften und Befehle der Elemente enthält.

 In [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Verwalten Sie Projekt Hierarchien mithilfe der Hierarchy-Schnittstelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> . Die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Schnittstelle leitet Befehle, die Sie von Projekt Elementen aufrufen, anstelle des Standard Befehls Handlers in das entsprechende Hierarchie Fenster um.

## <a name="project-hierarchies"></a>Projekt Hierarchien
 Jede Projekt Hierarchie enthält Elemente, die Sie anzeigen und bearbeiten können. Diese Elemente variieren abhängig vom Projekttyp. Ein Datenbankprojekt kann z. b. gespeicherte Prozeduren, Daten Bank Sichten und Datenbanktabellen enthalten. Ein Programmier Sprachprojekt hingegen enthält wahrscheinlich Quelldateien und Ressourcen Dateien für Bitmaps und Dialogfelder. Hierarchien können eingebettet werden, was Ihnen beim Erstellen einer Projekt Hierarchie zusätzliche Flexibilität bietet.

 Wenn Sie einen neuen Projekttyp erstellen, steuert der Projekttyp den gesamten Satz von Elementen, die darin bearbeitet werden können. Projekte können jedoch Elemente enthalten, für die Sie nicht über Bearbeitungs Unterstützung verfügen. Visual C++ Projekte können z. b. HTML-Dateien enthalten, auch wenn Visual C++ keinen angepassten Editor für den HTML-Dateityp bereitstellt.

 Hierarchien verwalten die Persistenz der Elemente, die Sie enthalten. Die Implementierung der Hierarchie muss alle besonderen Eigenschaften steuern, die sich auf die Persistenz der Elemente in der Hierarchie auswirken. Wenn die Elemente z. b. Objekte in einem Repository anstelle von Dateien darstellen, muss die Hierarchie Implementierung die Persistenz dieser Objekte steuern. Die IDE leitet die Hierarchie so um, dass die Elemente in Übereinstimmung mit der Benutzereingabe gespeichert werden, aber die IDE steuert keine Aktionen, die zum Speichern dieser Elemente erforderlich sind. Stattdessen befindet sich das Projekt in der Kontrolle.

 Wenn ein Benutzer ein Element in einem Editor öffnet, wird die Hierarchie, die dieses Element steuert, ausgewählt und zur aktiven Hierarchie. Die ausgewählte Hierarchie bestimmt den Satz von Befehlen, die für das Element zur Verfügung stehen. Wenn Sie den Fokus des Benutzers auf diese Weise nachverfolgen, kann die Hierarchie den aktuellen Kontext des Benutzers widerspiegeln.

## <a name="see-also"></a>Weitere Informationen
 [Projekttypen](../../extensibility/internals/project-types.md) [Auswahl und Währung in den IDE-](../../extensibility/internals/selection-and-currency-in-the-ide.md) [VSSDK-Beispielen](../../misc/vssdk-samples.md)
