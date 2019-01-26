---
title: Benutzerdefinierte Tools | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c192128ff4995a551b50df9347981405e321b703
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54933229"
---
# <a name="custom-tools"></a>Benutzerdefinierte tools
*Benutzerdefinierte Tools* können Sie ein Tool mit einem Element in einem Projekt verknüpfen und das Tool ausführen, wenn die Datei gespeichert wird. Bestimmte benutzerdefinierte Tools, auch bezeichnet als *Einzeldatei-Generatoren*, werden häufig zum Konvertierer implementieren, das Generieren von Code aus und umgekehrt verwendet. Beispielsweise Erstellen von Einzeldatei-Generatoren [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] und [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Quellcode aus der *Settings* und *resx* Dateien. Der generierte Quellcode enthält die stark typisierten Zugriff auf die Daten in die *Settings* und *resx* Dateien. Die [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] und [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Projekttypen unterstützen benutzerdefinierte Tools; [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Projekttypen nicht der Fall. Eigene Projekttypen können auch benutzerdefinierte Tools unterstützen.  
  
 Benutzerdefinierte Tools sind registrierte Komponenten, implementieren die `IVsSingleFileGenerator` Schnittstelle.  
  
 Benutzerdefinierte Tools zugeordnet sind eine `ProjectItem` oberflächenobjekts und Designer und Editoren entsprechen. Ein benutzerdefiniertes Tool erfordert, die durch dargestellte Datei eine `ProjectItem` als Eingabe und schreibt eine neue Datei, deren Name über erfolgt, die `DefaultExtension` Methode.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Implementieren von Einzeldatei-Generatoren](../../extensibility/internals/implementing-single-file-generators.md)  
 Beschreibt, wie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> Schnittstelle, um ein benutzerdefiniertes Tool zu implementieren.  
  
 [Registrieren Einzeldatei-Generatoren](../../extensibility/internals/registering-single-file-generators.md)  
 Stellt Beschreibungen für die Registrierungseinträge für ein benutzerdefiniertes Tool bereit.  
  
 [Machen Sie Typen für visuelle Designer](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 Erläutert, wie Projektsystemen visuelle Designer, Zugriff, die generierten Klassen und Typen durch temporäre PE (portable Executable)-Dateien unterstützen.  
  
 [Speichern Sie die Eigenschaft eines Projektelements](../../extensibility/persisting-the-property-of-a-project-item.md)  
 Zeigt, wie eine Projektelementeigenschaft, z. B. der Autor einer Quelldatei, in der Projektdatei beibehalten werden.  
  
## <a name="reference"></a>Referenz  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 Enthält Informationen über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>, der transformiert einer einzelnen Eingabedatei in eine einzelne Ausgabedatei, die kompiliert oder zu einem Projekt hinzugefügt werden kann.  
  
 <xref:EnvDTE.ProjectItem>  
 Erläutert die `ProjectItem` -Schnittstelle, die ein Element in einem Projekt darstellt.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 Enthält Informationen über die `DefaultExtension` Methode, die die Dateinamenerweiterung abruft, der den Namen der Ausgabedatei zugewiesen ist.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Erweitern von Projekten](../../extensibility/extending-projects.md)  
 Beschreibt, wie Codedateien und Ressourcendateien mithilfe von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]-Projekten und -Projektmappen organisiert werden und wie die Quellcodeverwaltung implementiert wird.