---
title: Projekt Typ Essentials | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 899d2758be1561d9b5fbda3280230333cc0ac8a3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="project-type-essentials"></a>Projekt Typ Essentials
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]enthält einige Projekttypen für Sprachen wie z. B. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] oder [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Außerdem können Sie eigene Projekttypen erstellen.  
  
 Wenn Sie nur benutzerdefinierte Befehle, Editoren und Toolfenster, hinzufügen möchten [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], können Sie dies tun, ohne einen neuen Projekttyp erstellen. Weitere Informationen finden Sie unter den folgenden Themen:  
  
-   [Befehle, Menüs und Symbolleisten](../../extensibility/internals/commands-menus-and-toolbars.md)  
  
-   [Editor- und Sprachdiensterweiterungen](../../extensibility/editor-and-language-service-extensions.md)  
  
-   [Erweitern und Anpassen von Toolfenstern](../../extensibility/extending-and-customizing-tool-windows.md)  
  
 Ebenso, wenn Sie das Verhalten des angegebenen anpassen möchten [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] und [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Projekttypen, erreichen Sie mit Project Untertypen. Weitere Informationen finden Sie unter [Projekt Untertypen](../../extensibility/internals/project-subtypes.md).  
  
 Müssen Sie einen neuen Projekttyp für Projekte, die auf einer anderen Sprache als erstellen [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] und [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] , wenn Sie eine oder mehrere der folgenden unterstützen möchten:  
  
-   Build  
  
-   Bereitstellung  
  
-   Mehrere Konfigurationen  
  
-   Quellcodeverwaltung  
  
-   Debuggen  
  
-   Projektelemente im Projektmappen-Explorer  
  
-   Die **Projekt öffnen** oder **neues Projekt** Dialogfelder  
  
-   Projekt Schachtelung  
  
-   Weitere Informationen zu den Funktionen der Projekttypen finden Sie hier:  
  
-   Projekttypen sind Objekte in einem VSPackage, die den Satz von Schnittstellen implementieren [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] erwartet. Wenn Sie c# verwenden, einen Projekttyp entwickeln, wird die Managed Package Framework Projektklassen implementieren Sie die erforderlichen Schnittstellen für Sie und ermöglichen es Ihnen, dass diese Implementierung erben. Weitere Informationen finden Sie unter [mithilfe des Managed Package Framework einen Projekttyp (c#) implementieren](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).  
  
-   Für C++-Entwickler arbeiten die Klassen in der Bibliothek HierUtil auf ähnliche Weise aus. Weitere Informationen finden Sie unter [nicht im Build: verwenden HierUtil7 Projektklassen zum Implementieren von einem Project-Typs (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
-   Projekttypen können Daten als normale Quellcodedateien unterstützen, die in eine Assembly .exe oder .dll erstellen. Beispielsweise [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Datenbankprojekte enthalten Verweise auf Skripts und Abfrage-Dateien, die auf dem Datenträger gespeichert und Befehle hinzufügen **Projektmappen-Explorer** zum Ausführen der Skripts und Abfragen für eine Datenbank, aber die Projekte nicht unterstützt Erstellen Sie Verhalten. Weitere Informationen finden Sie unter [öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md).  
  
-   Ein Projekt ist keine Dateien überhaupt nicht verwendet. Beispielsweise konnte ein Projekttyp alle ihre Daten in einer Datenbank speichern. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]bietet Projekttypen vollständig selbst bestimmen, wie sie Daten für die Projekte und Projektelemente beizubehalten. Weitere Informationen finden Sie unter [Projekt Typ Entwurfsentscheidungen](../../extensibility/internals/project-type-design-decisions.md).  
  
-   Projekttypen müssen Bereitstellen einer *Projekt Factory*, ist ein Objekt, das eine Instanz des Projekts erstellt geben bei jedem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wird geöffnet oder erstellt ein Projekt, das basierend auf diesen Projekttyp mitgeteilt. Weitere Informationen finden Sie unter [erstellen Instanzen von mithilfe von Project Projektfactorys](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
-   Projekttypen müssen Vorlagen für Projekte und Projektelemente angeben. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]die Vorlagen werden verwendet, wenn Benutzer neue Projekte erstellen und neuer Elemente zu vorhandenen Projekten hinzufügen. Weitere Informationen finden Sie unter [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
-   Projekttypen können mehrere Konfigurationen, z. B. Debug- und unterstützen. Benutzer können die verschiedenen Konfigurationen eines Projekts ändern, mithilfe von Eigenschaftenseiten, die Sie angeben. Weitere Informationen finden Sie unter [Konfigurationsoptionen verwalten](../../extensibility/internals/managing-configuration-options.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Bereitstellen von Projekttypen](../../extensibility/internals/deploying-project-types.md)