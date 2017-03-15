---
title: "Project Untertypen Design | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Projekt-Untertypen, Entwurf"
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
caps.latest.revision: 32
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 32
---
# Project Untertypen Design
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Projekt untertypen VSPackages können Projekte auf Grundlage des Microsoft Build Engine \(MSBuild\) erweitern.  Die Verwendung von Aggregation können Sie den Großteil des Projektsystems verwalteten Kern wiederverwenden, das in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] trotzdem das Verhalten für ein bestimmtes Szenario weiter anpassen implementiert wird.  
  
 Die folgenden Themen führen den grundlegenden Entwurf und Implementierung von untertypen Projekt einzeln aufgeführt:  
  
-   Projekt\-Untertyp\-Entwurf.  
  
-   Aggregation auf mehreren Ebenen.  
  
-   Schnittstellen unterstützen.  
  
## Projekt\-Untertyp\-Entwurf  
 Die Initialisierung eines Projekts untertyps wird erreicht, indem die wichtigsten <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> und die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>\-Objekten aggregiert.  Diese Aggregation kann ein Projekt untertyp, um die meisten Funktionen des Projekts Basisklasse zu überschreiben oder zu erweitern.  Projekt untertypen rufen die erste Möglichkeit, Eigenschaften, mit <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>mit Befehlen und <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget><xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>Projektelement und Verwaltung mithilfe <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>zu behandeln.  Projekt untertypen können auch erweitern:  
  
-   Projektkonfiguration Objekte.  
  
-   Anlagenabhängige Objekten.  
  
-   konfigurationsunabhängige Suchobjekte.  
  
-   automatisierungsobjekte Projekt.  
  
-   Auflistungen automatisierungseigenschaften Projekt.  
  
 Weitere Informationen über die Erweiterbarkeit von Projekt untertypen, finden Sie unter [Eigenschaften und Methoden, die vom Projekt Untertypen erweitert](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md).  
  
##### Richtliniendateien  
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Umgebung stellt ein Beispiel für das Erweitern des Projektsystems Basisklasse mit einem Projekt untertyp in seiner Implementierung von Richtliniendateien.  Eine Richtliniendatei kann die Strukturierung der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Umgebung, indem Funktionen verwaltet, die das Projektmappen\-Explorer\-, **Projekt hinzufügen** Dialogfeld, **Neues Element hinzufügen** Dialog Box und das Dialogfeld **Eigenschaften** enthalten.  Der Richtlinien untertyp überschreibt und erhöht diese Funktionen über <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>, `IOleCommandTarget` und <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Implementierungen.  
  
##### Aggregations\-Mechanismus  
 Der Projekt untertyp\-Aggregations Mechanismus für die Umgebung unterstützt mehrere Aggregationsebenen und ermöglicht so einen erweiterten von anderen Typ implementiert werden muss, Untertyp eines Projekts mit dem Typ.  Für die unterstützenden Objekte eines Projekts untertyps, wie <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>, sind für mehrere Ebenen der Überlagerung zu ermöglichen.  In Uebereinstimmung mit den Einschränkungen von COM\- und müssen COM\-Aggregation Regeln untertypen, Projekt\- und niedrigen Projekten gemeinsam programmiert werden, um den inneren Untertyp oder das niedrige Projekt ordnungsgemäß zu ermöglichen, die Teilnahme an Methodenaufrufe zu delegieren, und Verweiszähler zu verwalten.  Das heißt, muss das Projekt, aggregiert werden so programmiert werden, dass Aggregation zu unterstützen.  
  
 Die folgende Abbildung zeigt eine vereinfachte Darstellung einer Projekt untertyp aggregation auf mehreren Ebenen angegeben.  
  
 ![Grafik zu Visual Studio&#45;Mehrebenen&#45;Projekttyp](../../extensibility/internals/media/vs_multilevelprojectflavor.png "VS\_MultilevelProjectFlavor")  
Mehrstufiger Projekt\-Untertyp  
  
 Eine Projekt untertyp aggregation auf mehreren Ebenen besteht aus drei Ebenen, ein niedriges Projekt, das von einem Projekt untertyp aggregiert wird, profitieren von aggregiertes dann einen erweiterten Projekt untertyp.  Die Abbildung konzentriert sich auf einige der unterstützenden Schnittstellen, die als Teil der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Architektur der untertyp Projekt zur Verfügung gestellt werden.  
  
##### Bereitstellungs\-Mechanismen  
 Bei vielen der Projektsystem funktionalitäten, die von einem Projekt untertyp Bereitstellung sind Mechanismen erhöht werden.  Ein Projekt untertyp Mechanismen Bereitstellung beeinflussen, indem er Schnittstellen implementiert \(z. B. <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> Konfiguration und <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>\) abgerufen werden, indem die QueryInterface für <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>aufruft.  In einem Szenario, in dem das Projekt untertyp und erweiterte Projekt untertyp verschiedene Implementierungen von Konfigurationsinformationen hinzufügen, ruft das niedrige Projekt auf `QueryInterface` erweiterten `IUnknown`des Projekts untertyps an.  Wenn der innere Projekt untertyp die Implementierung der Konfiguration enthalten ist, die das niedrige Projekt um anfordert, delegiert der erweiterte untertyp Projekt zur Implementierung, die vom inneren Projekt untertyp bereitgestellt wird.  Wie ein Mechanismus, um den Zustand einer Aggregation beizubehalten, die an andere, alle Ebenen von untertypen Projekt mit <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> Build nicht implementieren, um verknüpfte XML\-Daten in die Projektdateien beizubehalten.  Weitere Informationen finden Sie unter [Beibehalten von Daten in der MSBuild\-Projektdatei](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md).  <xref:EnvDTE80.IInternalExtenderProvider> wird als Mechanismus implementiert, um extender Automatisierung von Projekt untertypen abzurufen.  
  
 In der folgenden Abbildung extender konzentriert sich auf die Automatisierung, das suchobjekt Projektkonfiguration Implementierung verwendet, insbesondere die vom Projekt untertypen, um das niedrige Projektsystem zu erweitern.  
  
 ![Grafik zu VS&#45;Projekttyp Automatisierungsextender](../../extensibility/internals/media/vs_projectflavorautoextender.png "VS\_ProjectFlavorAutoExtender")  
Projekt\-Untertyp\-Automatisierungs\-Extender.  
  
 Projektuntertypen können das niedrige Projektsystem weiter erweitern, indem sie das Automatisierungsobjektmodell erweitern.  Diese werden als Teil des DTE\-Automatisierungsobjekts definiert und verwendet werden, um das Projektobjekt, das `ProjectItem`\-Objekt und das `Configuration`\-Objekt zu erweitern.  Weitere Informationen finden Sie unter [Erweitern Sie das Objektmodell des Basis\-Projekts](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).  
  
## Aggregation auf mehreren Ebenen  
 Eine Implementierung der untertyp Projekt mit einem Projekt untertyp auf der untersten Ebene umschließt, muss sich kooperativ so programmiert werden, dass sie dem inneren Projekt untertyp zuzulassen, um ordnungsgemäß zu funktionieren.  Eine Liste der Programmierelement selbst enthält:  
  
-   Die <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> Implementierung des Projekts untertyps, der den inneren Untertyp umschließt, muss auf <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> die Implementierung des inneren Projekt untertyps für <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A><xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> und Methoden delegieren.  
  
-   Die <xref:EnvDTE80.IInternalExtenderProvider> Implementierung des Wrappers, untertyps muss auf dem des inneren Projekt untertyps delegieren.  Insbesondere muss die Implementierung von <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> die Zeichenfolge aus dem Namen der inneren Projekt untertyp abrufen und dann die Zeichenfolgen verketten, die er als Extender hinzufügen möchte.  
  
-   Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> Implementierung eines Wrapper untertyps muss das Projekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>\-Objekt des inneren Projekt untertyps instanziieren und sie als privaten Delegaten enthalten, da nur die grundlegenden Projektkonfiguration Objekt des Projekts direkt weiß, dass das Projekt Wrapper untertyp\-Konfigurations Objekt vorhanden ist.  Der äußere untertyp Projekt zunächst Schnittstellen Konfiguration auswählen kann, die er direkt behandeln möchte und delegiert dann den Rest auf die interne Implementierung des Projekts untertyps von <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>.  
  
## Schnittstellen unterstützen  
 Das niedrige Projekt zu unterstützenden Aufrufe delegiert Schnittstellen, die von einem Projekt untertyp hinzugefügt werden, um verschiedene Aspekte seiner Implementierung zu erweitern.  Dies schließt das Erweitern von Projektkonfiguration von Objekten und verschiedener Eigenschaftenbrowser Objekte ein.  Diese Schnittstellen werden abgerufen, indem `QueryInterface` auf `punkOuter` \(ein Zeiger auf `IUnknown`\) des äußersten Projekt untertyp aggregators aufruft.  
  
|Schnittstelle|Projekt\-Untertyp|  
|-------------------|-----------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Ermöglicht es dem Projekt untertyp to:<br /><br /> -   Stellen Sie eine Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> bereit.<br />-   Kontrollieren Sie den Start des Debuggers, indem Sie dem Projekt untertyp ermöglichen, ihre eigene Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>bereitzustellen.<br />-   Deaktivieren Sie ausdrucksauswertung Entwurfszeit geeignet, indem Sie den `DBGLAUNCH_DesignTimeExprEval` Fall in seiner Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>behandeln.|  
|<xref:EnvDTE80.IInternalExtenderProvider>|Ermöglicht es dem Projekt untertyp to:<br /><br /> -   Erweitern Sie <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> des Projekts, unabhängige Eigenschaften der Konfiguration des Projekts hinzuzufügen oder zu entfernen.<br />-   Erweitern Sie das<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>\(für\) des Projekts.<br /><br /> Die oben aufgeführten Eigenschaftswerte werden von <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>\-Enumeration bestimmt.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Ermöglicht dem Projekt untertyp der Zuordnung zurück an den angegebenen <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> das Objekt suchobjekt Projektkonfiguration.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Ermöglicht es dem Projekt untertyp der Zuordnung zurück an <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> oder dem `VSITEMID`\-Objekt mit dem suchobjekt Projektkonfiguration.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Ermöglicht dem Projekt untertyp willkürlich strukturierte Daten, um XML zur Projektdatei beizubehalten \(.vbproj oder .csproj\).  Dies ist keine Daten an MSBuild sichtbar.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Ermöglicht es dem Projekt untertyp to:<br /><br /> -   Hinzufügen neuer beibehalten werden soll, MSBuild\- Eigenschaften hinzu.<br />-   Entfernen Sie unnötige Eigenschaften von MSBuild.<br />-   Abfrage für einen aktuellen Wert einer MSBuild\-Eigenschaft.<br />-   Ändern Sie den aktuellen Wert einer MSBuild\-Eigenschaft.|  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>