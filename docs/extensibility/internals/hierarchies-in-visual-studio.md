---
title: Hierarchien in Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cdbb8a0e58f6b1e5bc6e32f8c319d1480c4db4b5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708187"
---
# <a name="hierarchies-in-visual-studio"></a>Hierarchien in Visual Studio
Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (IDE) zeigt ein Projekt als *Hierarchie*an. In der IDE ist eine Hierarchie eine Knotenstruktur, bei der jeder Knoten über einen Satz zugeordneter Eigenschaften verfügt. Eine *Projekthierarchie* ist ein Container, der die Elemente des Projekts, die Beziehungen der Elemente und die zugehörigen Eigenschaften und Befehle der Elemente enthält.

 In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]verwalten Sie Projekthierarchien mithilfe der <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>Hierarchieschnittstelle . Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Schnittstelle leitet Befehle, die Sie von Projektelementen aufrufen, an das entsprechende Hierarchiefenster anstelle des Standardbefehlshandlers um.

## <a name="project-hierarchies"></a>Projekthierarchien
 Jede Projekthierarchie enthält Elemente, die Sie anzeigen und bearbeiten können. Diese Elemente variieren je nach Projekttyp. Ein Datenbankprojekt kann z. B. gespeicherte Prozeduren, Datenbankansichten und Datenbanktabellen enthalten. Ein Programmsprache-Projekt hingegen wird wahrscheinlich Quelldateien und Ressourcendateien für Bitmaps und Dialogfelder enthalten. Hierarchien können geschachtelt werden, was Ihnen eine zusätzliche Flexibilität beim Erstellen einer Projekthierarchie bietet.

 Wenn Sie einen neuen Projekttyp erstellen, steuert der Projekttyp den vollständigen Satz von Elementen, die darin bearbeitet werden können. Projekte können jedoch Elemente enthalten, für die sie keine Bearbeitungsunterstützung haben. Beispielsweise können Visual C++-Projekte HTML-Dateien enthalten, obwohl Visual C++ keinen benutzerdefinierten Editor für den HTML-Dateityp bietet.

 Hierarchien verwalten die Persistenz von Elementen, die sie enthalten. Die Implementierung der Hierarchie muss alle speziellen Eigenschaften steuern, die sich auf die Persistenz der Elemente innerhalb der Hierarchie auswirken. Wenn die Elemente beispielsweise Objekte in einem Repository anstelle von Dateien darstellen, muss die Hierarchieimplementierung die Persistenz dieser Objekte steuern. Die IDE selbst weist die Hierarchie an, die Elemente in Übereinstimmung mit Benutzereingaben zu speichern, aber die IDE steuert keine Aktionen, die zum Speichern dieser Elemente erforderlich sind. Stattdessen hat das Projekt die Kontrolle.

 Wenn ein Benutzer ein Element in einem Editor öffnet, wird die Hierarchie, die dieses Element steuert, ausgewählt und wird zur aktiven Hierarchie. Die ausgewählte Hierarchie bestimmt den Satz von Befehlen, die für die Aktivierung des Elements verfügbar sind. Wenn Sie den Benutzerfokus auf diese Weise verfolgen, kann die Hierarchie den aktuellen Kontext des Benutzers widerspiegeln.

## <a name="see-also"></a>Weitere Informationen
- [Projekttypen](../../extensibility/internals/project-types.md)
- [Auswahl und Währung in der IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [VSSDK-Beispiele](https://github.com/Microsoft/VSSDK-Extensibility-Samples)
