---
title: Projekt-Untertypen Entwurf | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
caps.latest.revision: 32
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 126bee146d1f53233db3c14672f80da4c0d60e9e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="project-subtypes-design"></a>Projekt Untertypen Entwurf
Projekt Untertypen können VSPackages, Projekte, die basierend auf der Microsoft Build Engine (MSBuild) zu erweitern. Die Verwendung von Aggregation können Sie die Wiederverwendung des Großteil der verwalteten Core Projektsystem implementiert der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] noch immer noch das Verhalten für ein bestimmtes Szenario anpassen.  
  
 In den folgenden Themen ausführlich der grundlegende Design und Implementierung des Projekts Untertypen beschrieben:  
  
-   Entwerfen der Projekt-Untertyp.  
  
-   Die Aggregation mit mehreren Ebenen.  
  
-   Unterstützen von Schnittstellen.  
  
## <a name="project-subtype-design"></a>Projekt Untertyp Entwurf  
 Die Initialisierung eines Untertyps Projekt wird erreicht, indem Sie den Hauptknoten aggregieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> Objekte. Diese Aggregation ermöglicht es, einen Projektuntertyp zu überschreiben, oder erhöhen die meisten Funktionen des Basis-Projekts. Projekt Untertypen Abrufen der ersten Chance, zu Eigenschaften mit verarbeiten <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, Befehle mit <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>, und Verwenden von Project Item Management <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>. Projekt Untertypen können auch erweitern:  
  
-   Projekt-Konfigurationsobjekte.  
  
-   Die konfigurationsabhängigen-Objekte.  
  
-   Konfiguration unabhängig durchsuchen-Objekte.  
  
-   Projekt-Automatisierungsobjekte verwenden.  
  
-   Automation-Eigenschaft projektauflistungen.  
  
 Weitere Informationen zur Erweiterbarkeit von Projekt Untertypen finden Sie unter [Eigenschaften und Methoden erweitert, indem Projekt Untertypen](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md).  
  
##### <a name="policy-files"></a>Richtliniendateien  
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Umgebung bietet ein Beispiel für das Basisprojektsystem mit einem Projektuntertyp in seiner Implementierung von Richtliniendateien erweitern. Eine Richtliniendatei ermöglicht die Strukturierung der der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Umgebung durch die Verwaltung von Features, die im Projektmappen-Explorer enthalten **Projekt hinzufügen** (Dialogfeld), **neues Element hinzufügen** Dialogfeld und der  **Eigenschaften** (Dialogfeld). Der Untertyp der Richtlinie überschrieben und erweitert diese Funktionen auch über <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>, `IOleCommandTarget` und <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Implementierungen.  
  
##### <a name="aggregation-mechanism"></a>Aggregation-Mechanismus  
 Die Umgebung Projekt Untertyp Aggregation Mechanismus unterstützt mehrere Ebenen von Aggregation, sodass eine erweiterte Untertyp von weiteren flavoring ein Flavor-Projektsystem Projekt implementiert werden. Darüber hinaus die unterstützende Objekte eines Projekts Untertyp, z. B. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>, mehrere Ebenen von Strukturlayout zu ermöglichen. In Übereinstimmung mit den Einschränkungen des COM- und COM+ müssen Aggregationsregeln, Projekt-Untertypen und Basis-Projekten kooperativ programmiert werden, um den inneren Untertyp oder die Basis-Projekt ordnungsgemäß Delegieren von Methodenaufrufen und Verwalten von Verweiszähler teilnehmen aktivieren . Also muss das Projekt zu aggregierende zur Unterstützung der Aggregation programmiert werden.  
  
 Die folgende Abbildung zeigt eine schematische Darstellung einer mit mehreren Ebenen Projekt Untertyp Aggregation.  
  
 ![Grafik zu Visual Studio-Mehrebenen-Projekttyp](../../extensibility/internals/media/vs_multilevelprojectflavor.gif "VS_MultilevelProjectFlavor")  
Mit mehreren Ebenen Projektuntertyp  
  
 Eine Projekt mit mehreren Ebenen Untertyp Aggregation besteht aus drei Ebenen, eine Basis-Projekt, das durch einen Projektuntertyp aggregiert ist, dann wird durch ein Projektuntertyp des erweiterten weiter aggregiert. Die Abbildung konzentriert sich auf einige unterstützenden Schnittstellen, die als Teil einer bereitgestellt werden die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projekt Untertyp-Architektur.  
  
##### <a name="deployment-mechanisms"></a>Bereitstellungsmechanismen  
 Von vielen der Basisprojektsystem sind Funktionen erweitert, indem ein Projektuntertyp Bereitstellungsmechanismen. Ein Projektuntertyp beeinflusst Bereitstellungsmechanismen durch Konfigurationsschnittstellen implementieren (z. B. <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>) abgerufen, die durch Aufrufen von QueryInterface auf <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>. In einem Szenario, in dem andere Konfiguration Implementierungen mit den Untertyp des Projekts und Untertyp des erweiterten Projekts hinzufügen, ruft der Basisprojekt `QueryInterface` im erweiterten Projekt Untertyp `IUnknown`. Wenn der Projektuntertyp des inneren die Konfiguration Implementierung, von der das Basisprojekt angefordert wird enthält, delegiert Untertyp des erweiterten Projekts für die Implementierung von Untertyp des inneren Projekts bereitgestellt. Als Mechanismus, um den Status von einem Aggregationsebene zu einem anderen beibehalten, alle Ebenen der Projekt-Untertypen implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> beziehen Sie XML-Daten in den Projektdateien, Build nicht beibehalten werden. Weitere Informationen finden Sie unter [beibehalten von Daten in der MSBuild-Projektdatei](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md). <xref:EnvDTE80.IInternalExtenderProvider>wird als Mechanismus zum Abrufen von Automatisierungsextender aus dem Projekt Untertypen implementiert.  
  
 Die folgende Abbildung konzentriert sich auf die Automatisierung Extender Implementierung, das Projekt durchsuchen Konfigurationsobjekt insbesondere vom Projekt Untertypen verwendet, um das Basisprojektsystem zu erweitern.  
  
 ![Grafik zu VS-Projekttyp Automatisierungsextender](../../extensibility/internals/media/vs_projectflavorautoextender.gif "VS_ProjectFlavorAutoExtender")  
Projekt-Untertyp Automatisierungsextender.  
  
 Projekt Untertypen können das Basisprojektsystem durch Erweitern des Automatisierungsmodells für das Objekt weiter erweitern. Diese werden als Teil der DTE-Automatisierungsobjekt definiert und werden verwendet, um das Projektobjekt erweitern die `ProjectItem` Objekt und die `Configuration` Objekt. Weitere Informationen finden Sie unter [erweitern das Objektmodell des Projekts Base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).  
  
## <a name="multi-level-aggregation"></a>Mit mehreren Ebenen Aggregation  
 Eine Untertyp-Implementierung, die einen niedrigeren Ebene Projektuntertyp umschließt muss kooperativ so programmiert werden, können den Projektuntertyp innere ordnungsgemäß funktionieren. Eine Liste der Programmierung von Zuständigkeiten enthält:  
  
-   Die <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> Implementierung der Untertyp des Projekts, das den inneren Untertyp wrapping ist delegieren muss, um die <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> Implementierung der Untertyp des inneren Projekts für beide <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> Methoden.  
  
-   Die <xref:EnvDTE80.IInternalExtenderProvider> Implementierung des Untertyps Projekt Wrapper muss mit der die innere Projektuntertyp delegieren. Insbesondere wird die Implementierung von <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> muss die Zeichenfolge der Namen von der inneren Projektuntertyp abrufen und verkettet Sie dann die Zeichenfolgen, die sie als Extender hinzufügen möchte.  
  
-   Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> Implementierung eines Untertyps Projekt Wrapper muss Instanziieren der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> Objekt seine inneren Projekt Untertyp und halten Sie sie gedrückt als private Delegaten, da nur die Basisprojekt Projekt Konfigurationsobjekt direkt, dem bekannt ist der Wrapper Projekt-Untertyp Konfigurationsobjekt vorhanden ist. Untertyp des äußeren Projekts wählen Sie zunächst Konfigurationsschnittstellen direkt behandeln möchte und klicken Sie dann den Rest der inneren Projektuntertyp-Implementierung des delegieren kann <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>.  
  
## <a name="supporting-interfaces"></a>Unterstützung von Schnittstellen  
 Das Basisprojekt delegiert Aufrufe zur Unterstützung von Schnittstellen hinzugefügt, indem ein Projektuntertyp, um verschiedene Aspekte des seine Implementierung zu erweitern. Dies schließt die Erweiterung von Projekt-Konfigurationsobjekte und verschiedene Eigenschaft Modellbrowser-Objekte. Diese Schnittstellen werden abgerufen, indem Aufrufen `QueryInterface` auf `punkOuter` (ein Zeiger auf die `IUnknown`) von der äußersten Projekt Untertyp Aggregator.  
  
|Interface|Projektuntertyp|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Ermöglicht den Untertyp des Projekts auf:<br /><br /> -Geben Sie eine Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>.<br />-Steuern Sie den Start des Debuggers können Sie den Untertyp des Projekts eine eigene Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>.<br />-Deaktivieren Sie die ausdrucksauswertung zur Entwurfszeit durch entsprechend behandeln die `DBGLAUNCH_DesignTimeExprEval` in seiner Implementierung von Groß-/Kleinschreibung <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>.|  
|<xref:EnvDTE80.IInternalExtenderProvider>|Ermöglicht den Untertyp des Projekts auf:<br /><br /> – Erweitern der <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> des Projekts hinzufügen oder Entfernen von unabhängigen Konfigurationseigenschaften des Projekts.<br />-Erweitern Sie das Automation-Projektobjekt (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>) des Projekts.<br /><br /> Eigenschaftswerte, die oben genannten stammen aus <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> Enumeration.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Ermöglicht den Untertyp des Projekts wieder zuordnen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> Objekts, dem das Projekt durchsuchen Konfigurationsobjekt.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Ermöglicht den Untertyp des Projekts wieder zuordnen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> oder `VSITEMID` -Objekt, das Projekt durchsuchen Konfigurationsobjekt.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Ermöglicht den Untertyp des Projekts, um beliebige strukturierte XML-Daten in die Projektdatei (VBPROJ- oder csproj) beizubehalten. Diese Daten sind nicht für MSBuild sichtbar.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Ermöglicht den Untertyp des Projekts auf:<br /><br /> -Fügen Sie neue MSBuild-Eigenschaften beibehalten werden sollen.<br />-Entfernen Sie unnötige Eigenschaften von MSBuild.<br />-Abfrage nach einem aktuellen Wert der MSBuild-Eigenschaft.<br />-Ändern Sie den aktuellen Wert der MSBuild-Eigenschaft.|  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>