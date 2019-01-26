---
title: Projektuntertypen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c2e5151131efdab36a3c9e5cf646b1ca9bf94b5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54922716"
---
# <a name="project-subtypes"></a>Projektuntertypen
Projektuntertypen ermöglichen das Anpassen oder das Verhalten der Projektsysteme von flavor [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Anpassungen beinhalten das Speichern von zusätzlicher Daten in der Projektdatei, hinzufügen oder Filtern von Elementen in der **neues Element hinzufügen** Dialogfeld steuern, wie Assemblys debuggt und bereitgestellt, und erweitern das Projekt **Eigenschaft Seiten** Dialogfeld. VSPackages implementieren Projektuntertypen mit COM-Aggregation.  
  
> [!NOTE]
>  Das Visual C++-Projektsystem unterstützt Projektuntertypen nicht. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projektuntertypen verwendet SQL Server und Smart Device-Projekte umsetzen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Entwurf von Projektuntertypen](../../extensibility/internals/project-subtypes-design.md)  
 Beschreibt das Konzept von Projektuntertypen.  
  
 [Initialisierungssequenz von Projektuntertypen](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)  
 Beschreibt die programmgesteuerte Projekt Untertyp-Initialisierungssequenz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Umgebung.  
  
 [Eigenschaften und Methoden, die von Projektuntertypen erweitert werden](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)  
 Ausführliche Beschreibungen der Funktionen und Methoden, die am häufigsten mithilfe von Projektuntertypen erweitert.  
  
 [Beibehalten von Daten in der MSBuild-Projektdatei](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)  
 Beschreibt, wie Daten in einer Projektdatei beibehalten werden und wie Sie mit <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> die Daten in der Projektdatei für die Aggregationsebenen des Projekt-Untertyp beibehalten.  
  
 [Benutzeroberfläche für Projekteigenschaften](../../extensibility/internals/project-property-user-interface.md)  
 Beschreibt, wie Projektuntertypen für das Projekt ändern, können **Eigenschaftenseiten** Dialogfeld.  
  
 [Erweitern des Objektmodells des Basisprojekts](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)  
 Enthält Informationen zur Verwendung von Projektuntertypen Automatisierungsextender das Automatisierungsobjektmodell zu erweitern.  
  
 [Mitwirken am Dialogfeld „Neues Element hinzufügen“](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)  
 Beschreibt das Hinzufügen von Elementen, die **neues Element hinzufügen** Dialogfeld.  
  
 [Speichern von Daten in Projektdateien](../../extensibility/saving-data-in-project-files.md)  
 Erläutert, wie einem Projektuntertyp speichern und untertypspezifischen Daten in der Projektdatei mithilfe des Managed Package Framework (MPF) abrufen kann.  
  
 [Behandlung einer speziellen Bereitstellung](../../extensibility/internals/handling-specialized-deployment.md)  
 Erläutert, wie Projektuntertypen spezielle bereitstellungsverhalten durch die Implementierung bereitstellen können die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> Schnittstelle.  
  
 [Hinzufügen und Entfernen von Eigenschaftenseiten](../../extensibility/adding-and-removing-property-pages.md)  
 Beschreibt, hinzufügen und Entfernen von Eigenschaftenseiten im Projekt-Designer.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Projekttypen](../../extensibility/internals/project-types.md)  
 Enthält Links zu Themen, die mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projekte.