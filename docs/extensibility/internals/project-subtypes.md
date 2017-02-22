---
title: "Projekt-Untertypen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Projekte [Visual Studio SDK] Untertypen"
  - "Projekt-Untertypen [Visual Studio SDK]"
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# Projekt-Untertypen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Untertypen von Project können Sie die anpassen oder das Verhalten der Projektsysteme von flavor [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Anpassungen umfassen das Speichern von zusätzlicher Daten in der Projektdatei, hinzufügen oder Filtern von Elementen in der **Neues Element hinzufügen** Dialogfeld steuern, wie Assemblys gedebuggt und bereitgestellt, und erweitern das Projekt **Eigenschaftenseiten** \(Dialogfeld\). VSPackages implementieren Projekt Untertypen mit COM Aggregation.  
  
> [!NOTE]
>  Das Visual C\+\+\-Projektsystem unterstützt Projekt Untertypen nicht.[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projekt Untertypen verwendet zum Implementieren von SQL Server und Smart Device\-Projekte.  
  
## In diesem Abschnitt  
 [Project Untertypen Design](../../extensibility/internals/project-subtypes-design.md)  
 Beschreibt das Konzept der Projekt\-Untertypen.  
  
 [Initialisierungssequenz Projekt Untertypen](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)  
 Beschreibt die programmgesteuerte Projekt Untertyp Initialisierung von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Umgebung.  
  
 [Eigenschaften und Methoden, die vom Projekt Untertypen erweitert](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)  
 Bietet eine ausführliche Beschreibung der Funktionen und Methoden, die am häufigsten mithilfe von Project Untertypen erweitert.  
  
 [Beibehalten von Daten in der MSBuild\-Projektdatei](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)  
 Beschreibt, wie Daten in einer Projektdatei beibehalten und wie Sie <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> die Daten in der Datei in das Projekt Untertyp Aggregationsebenen beibehalten.  
  
 [Benutzeroberfläche des Projekt\-Eigenschaften](../../extensibility/internals/project-property-user-interface.md)  
 Beschreibt, wie das Projekt Untertypen des Projekts ändern können **Eigenschaftenseiten** \(Dialogfeld\).  
  
 [Erweitern Sie das Objektmodell des Basis\-Projekts](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)  
 Enthält Informationen zum Projekt Untertypen Automatisierungsextender erweitern das Automatisierungsobjektmodell verwenden können.  
  
 [Zu den im Dialogfeld Neues Element hinzufügen](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)  
 Beschreibt, wie Sie Elemente hinzufügen die **Neues Element hinzufügen** \(Dialogfeld\).  
  
 [Speichern von Daten in Projektdateien](../../extensibility/saving-data-in-project-files.md)  
 Erläutert, wie ein Projektuntertyp speichern und Abrufen von untertypspezifischen Daten in der Projektdatei mit dem Managed Package Framework \(MPF\) kann.  
  
 [Behandlung spezielle Bereitstellung](../../extensibility/internals/handling-specialized-deployment.md)  
 Erläutert, wie Project\-Untertypen spezielle bereitstellungsverhalten durch die Implementierung bereitstellen können die <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> Schnittstelle.  
  
 [Hinzufügen und Entfernen von Eigenschaftenseiten](../../extensibility/adding-and-removing-property-pages.md)  
 Beschreibt, hinzufügen und Entfernen von Eigenschaftenseiten im Projekt\-Designer.  
  
## Verwandte Abschnitte  
 [Projekttypen](../../extensibility/internals/project-types.md)  
 Enthält Links zu Themen, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projekte.