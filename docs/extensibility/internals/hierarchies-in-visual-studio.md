---
title: Hierarchien in Visual Studio | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 437372a5b88e58c12b7a7d34102d87afce5c086b
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2019
ms.locfileid: "56841778"
---
# <a name="hierarchies-in-visual-studio"></a>Hierarchien in Visual Studio
Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (IDE) zeigt ein Projekt als eine *Hierarchie*. In der IDE ist eine Hierarchie eine Struktur von Knoten, in dem jeder Knoten über einen Satz zugeordneter Eigenschaften verfügt. Ein *Projekt Hierarchie* ist ein Container, die Elemente des Projekts, die Elemente Beziehungen und zugeordneten Eigenschaften der Elemente und Befehle enthält.

 In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], verwalten Sie projekthierarchien, über die hierarchienschnittstelle, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Schnittstelle leitet Befehle, die Sie auf der entsprechenden hierachiefenster anstelle beim standardbefehlshandler von Projektelementen aufrufen.

## <a name="project-hierarchies"></a>Projekthierarchien
 Jedes Projekthierarchie enthält Elemente, die Sie anzeigen und bearbeiten können. Diese Elemente hängen vom Projekttyp ab. Ein Datenbankprojekt kann z. B. gespeicherte Prozeduren, Datenbanksichten und Datenbanktabellen enthalten. Eine Programmiersprache Projekt umfasst wahrscheinlich auf der anderen Seite Quelldateien und Ressourcendateien für Bitmaps und Dialogfelder. Hierarchien können geschachtelt werden, wo Sie einige zusätzliche Flexibilität bei der Erstellung einer Projekthierarchie.

 Wenn Sie einen neuen Projekttyp erstellen, steuert der Projekttyp den vollständigen Satz von Elementen, die es bearbeitet werden kann. Projekte können jedoch Elemente enthalten, für die sie keine Bearbeitung unterstützt. Visual C++-Projekte können z. B. HTML-Dateien enthalten, obwohl Visual C++ keine benutzerdefinierten Editor für den Typ des HTML-Datei bereitstellt.

 Hierarchien verwalten die Persistenz die enthaltenen Elemente. Die Implementierung der Hierarchie muss keine speziellen Eigenschaften steuern, die die Persistenz der Elemente innerhalb der Hierarchie auswirken. Wenn die Elemente, Objekte in einem Repository anstelle von Dateien darstellen, muss die Implementierung der Hierarchie z. B. die Dauerhaftigkeit der Objekte steuern. Die IDE selbst weist die Hierarchie der Elemente in Übereinstimmung mit der Benutzereingabe zu speichern, aber die IDE steuert keine Aktionen, die erforderlich sind, um diese Elemente zu speichern. Stattdessen wird das Projekt im Steuerelement.

 Wenn ein Benutzer ein Element in einem Editor geöffnet wird, wird die Hierarchie, die dieses Element steuert ausgewählt ist, und wird die aktive Hierarchie. Die ausgewählte Hierarchie bestimmt den Satz von Befehlen zum Reagieren auf das Element zur Verfügung. Nachverfolgen der den Benutzerfokus auf diese Weise kann die Hierarchie entsprechend der aktuelle Kontext des Benutzers.

## <a name="see-also"></a>Siehe auch
- [Projekttypen](../../extensibility/internals/project-types.md)
- [Auswahl und Aktualität in der IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [VSSDK-Beispiele](https://aka.ms/vs2015sdksamples)