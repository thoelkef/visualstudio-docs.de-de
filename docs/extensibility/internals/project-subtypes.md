---
title: Projektuntertypen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e91a16ad11f7089230138919519922d58f3cc472
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="project-subtypes"></a>Projekt Untertypen
Projekt Untertypen ermöglichen das Anpassen oder das Verhalten der Projektsysteme des flavor [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Anpassungen umfassen das Speichern von zusätzlicher Daten in der Projektdatei, hinzufügen oder Filtern von Elementen in der **neues Element hinzufügen** (Dialogfeld), die steuern, wie Assemblys gedebuggt und bereitgestellt, und erweitern das Projekt **Eigenschaft Seiten** (Dialogfeld). VSPackages implementieren Projekt Untertypen mit COM Aggregation.  
  
> [!NOTE]
>  Das Visual C++-Projektsystem unterstützt Untertypen von Project nicht. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] selbst verwendet Projekt Untertypen, um SQL Server und Smart Device-Projekte zu implementieren.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Entwurf von Projektuntertypen](../../extensibility/internals/project-subtypes-design.md)  
 Beschreibt das Konzept der Projekt-Untertypen.  
  
 [Initialisierungssequenz von Projektuntertypen](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)  
 Beschreibt die programmgesteuerte Projekt Untertyp Initialisierungssequenz von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Umgebung.  
  
 [Eigenschaften und Methoden, die von Projektuntertypen erweitert werden](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)  
 Enthält ausführliche Beschreibungen der Funktionen und Methoden, die am häufigsten mit Projekt Untertypen erweitert.  
  
 [Beibehalten von Daten in der MSBuild-Projektdatei](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)  
 Beschreibt, wie Daten in einer Projektdatei beibehalten und wie <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> die Daten in der Projektdatei für das Projekt Untertyp Aggregationsebenen beibehalten.  
  
 [Benutzeroberfläche für Projekteigenschaften](../../extensibility/internals/project-property-user-interface.md)  
 Beschreibt, wie das Projekt Untertypen des Projekts ändern können **Eigenschaftenseiten** (Dialogfeld).  
  
 [Erweitern des Objektmodells des Basisprojekts](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)  
 Enthält Informationen zur Verwendung von Project Untertypen Automatisierungsextender Automatisierungsobjektmodell erweitern.  
  
 [Mitwirken am Dialogfeld „Neues Element hinzufügen“](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)  
 Enthält Informationen zum Hinzufügen von Elementen, die **neues Element hinzufügen** (Dialogfeld).  
  
 [Speichern von Daten in Projektdateien](../../extensibility/saving-data-in-project-files.md)  
 Erläutert, wie ein Projektuntertyp speichern und Abrufen von untertypspezifischen Daten in der Projektdatei mit dem Managed Package Framework (MPF) kann.  
  
 [Behandlung einer speziellen Bereitstellung](../../extensibility/internals/handling-specialized-deployment.md)  
 Erläutert, wie Project Untertypen spezielle bereitstellungsverhalten durch die Implementierung bereitstellen können, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> Schnittstelle.  
  
 [Hinzufügen und Entfernen von Eigenschaftenseiten](../../extensibility/adding-and-removing-property-pages.md)  
 Beschreibt, hinzufügen und Entfernen von Eigenschaftenseiten im Projekt-Designer.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Projekttypen](../../extensibility/internals/project-types.md)  
 Enthält Links zu Themen, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projekte.