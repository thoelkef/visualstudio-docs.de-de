---
title: Projekt Untertypen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5ad1e105d43c40782b13d8799b20626e57363c2f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840857"
---
# <a name="project-subtypes"></a>Projektuntertypen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Mit Projekt Untertypen können Sie das Verhalten der Projektsysteme von anpassen oder anpassen [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Zu den Anpassungen gehören das Speichern zusätzlicher Daten in der Projektdatei, das Hinzufügen oder Filtern von Elementen im Dialogfeld **Neues Element hinzufügen** , das Steuern der Deserialisierung und Bereitstellung von Assemblys und das Erweitern des Dialog Felds **Eigenschaften Seiten** für Projekt VSPackages implementieren Projekt Untertypen mithilfe von com-Aggregationen.  
  
> [!NOTE]
> Projekt Untertypen werden vom Visual C++-Projekt System nicht unterstützt. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] selbst verwendet Projekt Untertypen, um SQL Server-und Smart Device-Projekte zu implementieren.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Entwurf von Projektuntertypen](../../extensibility/internals/project-subtypes-design.md)  
 Beschreibt das Konzept von Projekt Untertypen.  
  
 [Initialisierungssequenz von Projektuntertypen](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)  
 Beschreibt die Initialisierungs Sequenz des programmatischen Projekt unter Typs nach [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Umgebung.  
  
 [Eigenschaften und Methoden, die von Projektuntertypen erweitert werden](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)  
 Stellt ausführliche Beschreibungen der Features und Methoden bereit, die am häufigsten mithilfe von Projekt Untertypen erweitert werden.  
  
 [Beibehalten von Daten in der MSBuild-Projektdatei](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)  
 Beschreibt, wie Daten in einer Projektdatei persistent gespeichert werden und wie verwendet wird, <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> um die Daten in der Projektdatei über die Aggregations Ebenen des Projekt unter Typs hinweg beizubehalten.  
  
 [Benutzeroberfläche für Projekteigenschaften](../../extensibility/internals/project-property-user-interface.md)  
 Beschreibt, wie Projekt Untertypen das Dialogfeld **Eigenschaften Seiten** des Projekts ändern können.  
  
 [Erweitern des Objektmodells des Basisprojekts](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)  
 Stellt Informationen dazu bereit, wie Projekt Untertypen automatisierungsexextender zum Erweitern des Automatisierungs Objektmodells verwenden können.  
  
 [Mitwirken am Dialogfeld „Neues Element hinzufügen“](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)  
 Beschreibt das Hinzufügen von Elementen zum Dialogfeld **Neues Element hinzufügen** .  
  
 [Speichern von Daten in Projektdateien](../../extensibility/saving-data-in-project-files.md)  
 Erläutert, wie ein Projekt Untertyp unter typspezifische Daten in der Projektdatei mithilfe des Managed Package Framework (MPF) speichern und abrufen kann.  
  
 [Behandlung einer speziellen Bereitstellung](../../extensibility/internals/handling-specialized-deployment.md)  
 Erläutert, wie Projekt Untertypen ein spezielles Bereitstellungs Verhalten durch Implementieren der-Schnittstelle bereitstellen können <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> .  
  
 [Hinzufügen und Entfernen von Eigenschaftenseiten](../../extensibility/adding-and-removing-property-pages.md)  
 Beschreibt das Hinzufügen und Entfernen von Eigenschaften Seiten im Projekt-Designer.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Projekttypen](../../extensibility/internals/project-types.md)  
 Enthält Links zu Themen, in denen-Projekte erläutert werden [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .
