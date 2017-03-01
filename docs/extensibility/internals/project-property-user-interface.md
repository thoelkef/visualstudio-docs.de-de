---
title: Eigenschaftenseite Projekt | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: b344731061053abb208225a0480408ebbe682050
ms.lasthandoff: 02/22/2017

---
# <a name="project-property-user-interface"></a>Benutzeroberfläche des Projekt-Eigenschaften
Ein Projektuntertyp können Sie mithilfe der Elemente im Projekt **Eigenschaftenseiten** (Dialogfeld), wie sie vom Basis-Projekt bereitgestellt werden ausblenden oder schreibgeschützte Steuerelemente und ganze Seiten angegeben oder hinzufügen Projekt Untertyp-spezifische Seiten der **Eigenschaftenseiten** im Dialogfeld.  
  
## <a name="extending-the-project-property-dialog-box"></a>Erweitern Sie im Dialogfeld Projekt  
 Ein Projektuntertyp implementiert Automatisierungsextender und Projekt Konfigurationsobjekte durchsuchen. Diese Extender implementieren die <xref:EnvDTE.IFilterProperties>Schnittstelle, damit bestimmte Eigenschaften ausgeblendet oder schreibgeschützt.</xref:EnvDTE.IFilterProperties> Die **Eigenschaftenseiten** im Dialogfeld des Basis-Projekts vom Basis-Projekt implementiert berücksichtigt die Filterung ausgeführt, indem die Automatisierungsextender.  
  
 Der Prozess zur Verlängerung des ein **Projekteigenschaft** wird im Dialogfeld unten erläutert:  
  
-   Das Basis-Projekt Ruft die Extender aus den Untertyp des Projekts ab, durch die Implementierung der <xref:EnvDTE80.IInternalExtenderProvider>Schnittstelle.</xref:EnvDTE80.IInternalExtenderProvider> Das Durchsuchen, Projekt-Automatisierung und Projekt durchsuchen Konfigurationsobjekte des Basis-Projekts alle implementieren diese Schnittstelle.  
  
-   Die Implementierung von <xref:EnvDTE80.IInternalExtenderProvider>für das Projekt durchsuchen-Objekt und das Projekt Automatisierungsobjekt zu delegieren der <xref:EnvDTE80.IInternalExtenderProvider>Implementierung des Projekts Untertyp Aggregators (d. h. sie `QueryInterface` für <xref:EnvDTE80.IInternalExtenderProvider>auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>Project-Objekt).</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> </xref:EnvDTE80.IInternalExtenderProvider> </xref:EnvDTE80.IInternalExtenderProvider> </xref:EnvDTE80.IInternalExtenderProvider>  
  
-   Implementiert das Basisprojekt durchsuchen Konfigurationsobjekt auch <xref:EnvDTE80.IInternalExtenderProvider>, direkt in den Automatisierungsextender aus dem Projekt Untertyp Configuration-Objekt zu aktivieren.</xref:EnvDTE80.IInternalExtenderProvider> Ihre Implementierung delegiert an die <xref:EnvDTE80.IInternalExtenderProvider>Schnittstelle implementiert, die vom Projekt Untertyp Aggregator.</xref:EnvDTE80.IInternalExtenderProvider>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, durch das Projekt durchsuchen Konfigurationsobjekt, gibt implementiert die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>Objekt.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy></xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, auch vom Projekt Konfiguration durchsuchen Objekt implementiert, gibt die <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>Objekt.</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg></xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>  
  
-   Ein Projektuntertyp kann die entsprechenden CATIDs für die verschiedenen erweiterbare Objekte des Basis-Projekts zur Laufzeit bestimmen, indem Folgendes abrufen <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>Werte:</xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2></xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2></xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2></xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
 Um die CATIDs für den Projektumfang zu ermitteln, ruft den Untertyp des Projekts die oben aufgeführten Eigenschaften für <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>aus der `VSITEMID``typedef`.</xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT> Ein Projektuntertyp sollten auch zu bestimmen, welche **Eigenschaftenseiten** Dialogfeld für das Projekt angezeigt werden abhängig von der Konfiguration und unabhängige Konfiguration. Einige Projekt Untertypen müssen integrierte Seiten entfernen und Projekt Untertyp bestimmte Seiten hinzufügen. Damit dies die Aufrufe der verwaltete Client-Projekt können die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>Methode für die folgenden Eigenschaften:</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>  
  
-   `VSHPROPID_PropertyPagesCLSIDList`– eine durch Semikolons getrennte Liste der CLSIDs konfigurationsunabhängige Eigenschaftenseiten.  
  
-   `VSHPROPID_CfgPropertyPagesCLSIDList —`eine durch Semikolons getrennte Liste CLSIDs konfigurationsabhängig Eigenschaftenseiten.  
  
 Da das Projekt Aggregaten Untertyp der <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>-Objekt können sie die Definition dieser Eigenschaften zu bestimmen, welche überschreiben **Eigenschaftenseiten** Dialogfelder angezeigt werden.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Den Untertyp des Projekts kann Abrufen dieser Eigenschaften aus dem inneren Basis-Projekt, und klicken Sie dann hinzufügen oder Entfernen von CLSIDs nach Bedarf.  
  
 Neue Eigenschaftenseiten hinzugefügt, indem ein Projektuntertyp werden von der Implementierung des Basis-Projekt ein Projekt durchsuchen Konfigurationsobjekt übergeben. Dieses Projekt durchsuchen Konfigurationsobjekt unterstützt Automatisierungsextender. Weitere Informationen zu AutomationExtenders, finden Sie unter [implementieren und Verwenden von Automatisierungsextendern](http://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356). Die Eigenschaftenseiten, die durch den Aufruf der Projekt-Untertyp implementiert <xref:EnvDTE.Project.Extender%2A>ihre eigenen Projekt Untertyp durchsuchen Konfigurationsobjekt abgerufen, die das Konfigurationsobjekt Durchsuchen des Basis-Projekts erweitert.</xref:EnvDTE.Project.Extender%2A>  
  
## <a name="see-also"></a>Siehe auch  
 <xref:EnvDTE.IFilterProperties></xref:EnvDTE.IFilterProperties>   
 [Property Pages Dialog Box](http://msdn.microsoft.com/en-us/4a3d34ac-ed03-45e8-ae60-a0e1aad300e4)
