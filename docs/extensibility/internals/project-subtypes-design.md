---
title: Projektuntertypen Design | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b939d197bfd7e58b555ca7698f08643e3d38ef2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706445"
---
# <a name="project-subtypes-design"></a>Entwurf von Projektuntertypen

Mit Projektuntertypen können VSPackages Projekte auf der Grundlage der Microsoft Build Engine (MSBuild) erweitern. Mit der Verwendung der Aggregation können Sie den Großteil [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] des verwalteten Kernprojektsystems wiederverwenden, in dem sie implementiert sind, aber dennoch das Verhalten für ein bestimmtes Szenario anpassen.

 In den folgenden Themen werden der grundlegende Entwurf und die Implementierung von Projektuntertypen erläutert:

- Projekt-Untertypentwurf.

- Aggregation auf mehreren Ebenen.

- Unterstützende Schnittstellen.

## <a name="project-subtype-design"></a>Projekt-Subtype-Entwurf

Die Initialisierung eines Projektsubtyps wird durch <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> Aggregieren von Haupt- und Objekten erreicht. Diese Aggregation ermöglicht es einem Projektuntertyp, die meisten Funktionen des Basisprojekts zu überschreiben oder zu erweitern. Projektuntertypen erhalten die erste Möglichkeit, Eigenschaften mithilfe von <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, Befehlen mit <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> und und <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>der Projektelementverwaltung mithilfe <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>zu behandeln. Projektuntertypen können sich auch erweitern:

- Projektkonfigurationsobjekte.

- Konfigurationsabhängige Objekte.

- Konfigurationsunabhängige Suchobjekte.

- Projektautomatisierungsobjekte.

- Projektautomatisierungseigenschaftssammlungen.

Weitere Informationen zur Erweiterbarkeit nach Projektuntertypen finden Sie unter [Eigenschaften und Methoden, die von Projektuntertypen erweitert](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)werden.

### <a name="policy-files"></a>Richtliniendateien

Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Umgebung bietet ein Beispiel für die Erweiterung des Basisprojektsystems um einen Projektuntertyp bei der Implementierung von Richtliniendateien. Eine Richtliniendatei ermöglicht die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Gestaltung der Umgebung, indem Features verwaltet werden, die den Projektmappen-Explorer, das Dialogfeld **Projekt hinzufügen,** das Dialogfeld **Neues Element hinzufügen** und das Dialogfeld **Eigenschaften** verwenden. Der Richtlinienuntertyp überschreibt und erweitert <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> `IOleCommandTarget` diese <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Features durch , und Implementierungen.

### <a name="aggregation-mechanism"></a>Aggregationsmechanismus

Der Projektsubtypaggregationsmechanismus der Umgebung unterstützt mehrere Aggregationsebenen, sodass ein erweiterter Subtyp durch weitere Aromaung eines aromatisierten Projekts implementiert werden kann. Außerdem sind die unterstützenden Objekte eines <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>Projektuntertyps, z. B. , so konzipiert, dass mehrere Ebenen der Schichtung möglich sind. Entsprechend den Einschränkungen der COM- und COM-Aggregationsregeln müssen Projektuntertypen und Basisprojekte kooperativ programmiert werden, damit der innere Subtyp oder das Basisprojekt ordnungsgemäß an der Delegierung von Methodenaufrufen und der Verwaltung von Referenzanzahlen teilnehmen kann. Das heißt, das Projekt, das kurz vor der Zusammenführung steht, muss programmiert werden, um die Aggregation zu unterstützen.

Die folgende Abbildung zeigt eine schematische Darstellung einer mehrstufigen Projektsubtypaggregation.

![Grafik zu Visual Studio-Mehrebenen-Projekttyp](../../extensibility/internals/media/vs_multilevelprojectflavor.gif)

Eine mehrstufige Projektsubtype-Aggregation besteht aus drei Ebenen, einem Basisprojekt, das von einem Projektuntertyp aggregiert und dann weiter von einem erweiterten Projektuntertyp aggregiert wird. Die Abbildung konzentriert sich auf einige der unterstützenden Schnittstellen, die als Teil der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projektsubtype-Architektur bereitgestellt werden.

### <a name="deployment-mechanisms"></a>Bereitstellungsmechanismen

Zu vielen Funktionen des Basisprojektsystems, die durch einen Projektuntertyp erweitert werden, gehören Bereitstellungsmechanismen. Ein Projektuntertyp beeinflusst Bereitstellungsmechanismen, indem <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> Konfigurationsschnittstellen (z. B. <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>und ) implementiert werden, die durch Aufrufen von QueryInterface unter abgerufen werden. In einem Szenario, in dem sowohl der Projektuntertyp als auch der `QueryInterface` erweiterte Projektuntertyp unterschiedliche `IUnknown`Konfigurationsimplementierungen hinzufügen, ruft das Basisprojekt den erweiterten Projektuntertyp auf. Wenn der innere Projektuntertyp die Konfigurationsimplementierung enthält, die das Basisprojekt fordert, delegiert der erweiterte Projektuntertyp an die Implementierung, die vom inneren Projektuntertyp bereitgestellt wird. Als Mechanismus zum Beibehalten des Status von einer Aggregationsebene zur <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> anderen implementieren alle Ebenen von Projektuntertypen, um nicht buildbezogene XML-Daten in den Projektdateien beizubehalten. Weitere Informationen finden Sie unter [Persistente Daten in der MSBuild-Projektdatei](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md). <xref:EnvDTE80.IInternalExtenderProvider>ist als Mechanismus zum Abrufen von Automatisierungs-Extendern aus den Projektuntertypen implementiert.

Die folgende Abbildung konzentriert sich auf die Implementierung des Automatisierungs-Extenders, insbesondere auf das Suchobjekt der Projektkonfiguration, das von Projektuntertypen verwendet wird, um das Basisprojektsystem zu erweitern.

![Grafik zu VS-Projekttyp Automatisierungsextender](../../extensibility/internals/media/vs_projectflavorautoextender.gif)

Projektuntertypen können das Basisprojektsystem weiter erweitern, indem sie das Automatisierungsobjektmodell erweitern. Diese werden als Teil des DTE-Automatisierungsobjekts definiert und `ProjectItem` zum Erweitern `Configuration` des Project-Objekts, des Objekts und des Objekts verwendet. Weitere Informationen finden Sie unter [Erweitern des Objektmodells des Basisprojekts](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).

## <a name="multi-level-aggregation"></a>Mehrstufige Aggregation

Eine Projektsubtype-Implementierung, die einen Projektuntertyp auf niedrigerer Ebene umschließt, muss kooperativ programmiert werden, damit der innere Projektuntertyp ordnungsgemäß funktionieren kann. Eine Liste der Programmieraufgaben umfasst:

- Die <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> Implementierung des Projektsubtyps, der den inneren <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> Subtype umschließt, muss <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> für <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> beide und Methoden an die Implementierung des inneren Projektsubtyps delegiert werden.

- Die <xref:EnvDTE80.IInternalExtenderProvider> Implementierung des Wrapperprojektuntertyps muss an den des inneren Projektuntertyps delegiert werden. Insbesondere muss die <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> Implementierung von anforderungen die Namenszeichenfolge aus dem inneren Projektuntertyp abrufen und dann die Zeichenfolgen verketten, die es als Extender hinzufügen möchte.

- Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> Implementierung eines Wrapperprojektsubtyps muss <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> das Objekt des inneren Projektsubtyps instanziieren und als privaten Delegaten speichern, da nur das Projektkonfigurationsobjekt des Basisprojekts direkt weiß, dass das Konfigurationsobjekt des Wrapperprojekts vorhanden ist. Der äußere Projektuntertyp kann zunächst Konfigurationsschnittstellen auswählen, die er direkt behandeln möchte, und den <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>Rest dann an die Implementierung von des inneren Projektuntertyps delegieren.

## <a name="supporting-interfaces"></a>Unterstützende Schnittstellen

Das Basisprojekt delegiert Aufrufe zur Unterstützung von Schnittstellen, die von einem Projektuntertyp hinzugefügt werden, um verschiedene Aspekte seiner Implementierung zu erweitern. Dazu gehört das Erweitern von Projektkonfigurationsobjekten und verschiedenen Eigenschaftenbrowserobjekten. Diese Schnittstellen werden abgerufen, `punkOuter` indem ein Zeiger `IUnknown`auf den ) des subtype aggregators des äußersten Projekts aufgerufen `QueryInterface` wird.

|Schnittstelle|Projekt-Untertyp|
|---------------|---------------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Ermöglicht dem Projektuntertyp:<br /><br /> - Bereitstellung einer <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>Implementierung von .<br />- Steuern Sie den Start des Debuggers, indem Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>dem Projektuntertyp erlauben, seine eigene Implementierung von bereitzustellen.<br />- Deaktivieren Sie die Entwurfszeitausdrucksauswertung, indem Sie den Fall bei der `DBGLAUNCH_DesignTimeExprEval` Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>entsprechend behandeln.|
|<xref:EnvDTE80.IInternalExtenderProvider>|Ermöglicht dem Projektuntertyp:<br /><br /> - Erweitern <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject> Sie das Projekt, um konfigurationsunabhängige Eigenschaften des Projekts hinzuzufügen oder zu entfernen.<br />- Erweitern Sie das<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtObject>Projektautomatisierungsobjekt ( ) des Projekts.<br /><br /> Die oben genannten <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> Eigenschaftswerte werden der Enumeration entnommen.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Ermöglicht dem Projektuntertyp, dem <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> Objekt, das dem Suchobjekt der Projektkonfiguration zugeordnet wurde, wieder zuzuordnen.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Ermöglicht dem Projektuntertyp die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Zuordnung `VSITEMID` zum oder dem Objekt, wenn das Suchobjekt der Projektkonfiguration angezeigt wird.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Ermöglicht dem Projektuntertyp, beliebige XML-strukturierte Daten in der Projektdatei (.vbproj oder .csproj) beizubehalten. Diese Daten sind für MSBuild nicht sichtbar.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Ermöglicht dem Projektuntertyp:<br /><br /> - Fügen Sie neue MSBuild-Eigenschaften hinzu, die beibehalten werden sollen.<br />- Entfernen Sie unnötige Eigenschaften aus MSBuild.<br />- Abfrage eines aktuellen Werts einer MSBuild-Eigenschaft.<br />- Ändern Sie den aktuellen Wert einer MSBuild-Eigenschaft.|

## <a name="see-also"></a>Weitere Informationen

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>
