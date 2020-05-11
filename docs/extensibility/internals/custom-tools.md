---
title: Benutzerdefinierte Werkzeuge | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e60f1d8cb8b25ed50b0b20c5ebb538286687ad72
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708961"
---
# <a name="custom-tools"></a>Benutzerdefinierte Tools
*Mit benutzerdefinierten Tools* können Sie ein Werkzeug einem Element in einem Projekt zuordnen und dieses Tool ausführen, wenn die Datei gespeichert wird. Bestimmte benutzerdefinierte Tools, manchmal auch als *Einzeldateigeneratoren*bezeichnet, werden häufig verwendet, um Übersetzer zu implementieren, die Code aus Daten generieren und umgekehrt. Beispielsweise [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] erstellen Einzeldateigeneratoren aus [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] den *.settings-* und *.resx-Dateien* . Der generierte Quellcode bietet stark typisierten Zugriff auf die Daten in den *.settings-* und *.resx-Dateien.* Die [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] und die Projekttypen unterstützen benutzerdefinierte Tools. [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Projekttypen nicht. Ihre eigenen Projekttypen können auch benutzerdefinierte Tools unterstützen.

 Benutzerdefinierte Tools sind registrierte `IVsSingleFileGenerator` Komponenten, die die Schnittstelle implementieren.

 Benutzerdefinierte Tools sind `ProjectItem` einem Schnittstellenobjekt zugeordnet und wie Designer und Editoren. Ein benutzerdefiniertes Tool nimmt `ProjectItem` die Datei, die durch eine Eingabe `DefaultExtension` dargestellt wird, und schreibt eine neue Datei, deren Dateiname von der Methode bereitgestellt wird.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Implementieren von Single-File-Generatoren](../../extensibility/internals/implementing-single-file-generators.md)

 Beschreibt, wie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> die Schnittstelle zum Implementieren eines benutzerdefinierten Tools verwendet wird.

- [Registrieren einzelner Dateigeneratoren](../../extensibility/internals/registering-single-file-generators.md)

 Enthält Beschreibungen für alle Registrierungseinträge für ein benutzerdefiniertes Tool.

- [Verfügbar machen von Typen für visuelle Designer](../../extensibility/internals/exposing-types-to-visual-designers.md)

 Erläutert, wie Projektsysteme visuelle nutzer stellen, um über temporäre portable ausführbare Dateien (PE) auf generierte Klassen und Typen zuzugreifen.

- [Beibehalten der Eigenschaft eines Projektelements](../../extensibility/persisting-the-property-of-a-project-item.md)

 Zeigt, wie eine Projektelementeigenschaft, z. B. der Autor einer Quelldatei, in der Projektdatei beibehalten wird.

## <a name="reference"></a>Referenz
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>Enthält Details <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>zu der , die eine einzelne Eingabedatei in eine einzelne Ausgabedatei transformiert, die kompiliert oder einem Projekt hinzugefügt werden kann.

 <xref:EnvDTE.ProjectItem>Erläutert `ProjectItem` die Schnittstelle, die ein Element in einem Projekt darstellt.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>Enthält Details `DefaultExtension` zur Methode, die die Dateinamenerweiterung abruft, die dem Ausgabedateinamen gegeben wird.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Erweitern von Projekten](../../extensibility/extending-projects.md)

 Beschreibt, wie Codedateien und Ressourcendateien mithilfe von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]-Projekten und -Projektmappen organisiert werden und wie die Quellcodeverwaltung implementiert wird.
