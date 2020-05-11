---
title: Benutzeroberfläche für Projekteigenschaft | Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4634eb5edaab16752bc5df82d70371a580845d28
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706400"
---
# <a name="project-property-user-interface"></a>Benutzeroberfläche für Projekteigenschaften

Ein Projektuntertyp kann die Elemente im Dialogfeld **Eigenschaftenseiten** des Projekts verwenden, wie sie vom Basisprojekt bereitgestellt werden, schreibgeschützte Steuerelemente und ganze Seiten wie angegeben ausblenden oder erstellen oder projektuntertypspezifische Seiten zum Dialogfeld **Eigenschaftenseiten** hinzufügen.

## <a name="extending-the-project-property-dialog-box"></a>Erweitern des Dialogfelds "Projekteigenschaft"

Ein Projektuntertyp implementiert Automatisierungs-Extender und Projektkonfigurationssuchobjekte. Diese Extender implementieren <xref:EnvDTE.IFilterProperties> die Schnittstelle, um bestimmte Eigenschaften ausgeblendet oder schreibgeschützt zu machen. Das Dialogfeld **Eigenschaftenseiten** des Basisprojekts, das vom Basisprojekt implementiert wird, berücksichtigt die Filterung, die von den Automation Extendern ausgeführt wird.

Der Vorgang der Erweiterung eines **Dialogfelds "Projekteigenschaft"** wird unten beschrieben:

- Das Basisprojekt ruft die Extender aus dem Projektuntertyp ab, indem die Schnittstelle implementiert wird. <xref:EnvDTE80.IInternalExtenderProvider> Die Such-, Projektautomatisierungs- und Projektkonfigurationsobjekte des Basisprojekts implementieren diese Schnittstelle.

- Die Implementierung <xref:EnvDTE80.IInternalExtenderProvider> von für das Projekt suchobjekt und <xref:EnvDTE80.IInternalExtenderProvider> das Projektautomatisierungsobjekt delegiert an `QueryInterface` <xref:EnvDTE80.IInternalExtenderProvider> die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Implementierung des Projektsubtypaggregators (d. h. sie für das Projektobjekt).

- Das Suchobjekt für die <xref:EnvDTE80.IInternalExtenderProvider> Basisprojektkonfiguration implementiert auch, um direkt im Automation Extender aus dem Projektsubtype-Konfigurationsobjekt zu verdrahten. Die Implementierung delegiert die Schnittstelle, <xref:EnvDTE80.IInternalExtenderProvider> die vom Projektsubtypaggregator implementiert wird.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, das vom Suchobjekt der <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Projektkonfiguration implementiert wird, gibt das Objekt zurück.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, das auch vom Suchobjekt der <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> Projektkonfiguration implementiert wird, gibt das Objekt zurück.

- Ein Projektuntertyp kann die entsprechenden CATIDs für die verschiedenen erweiterbaren Objekte <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> des Basisprojekts zur Laufzeit bestimmen, indem die folgenden Werte abgerufen werden:

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_ExtObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_BrowseObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_CfgBrowseObjectCATID>

Um die CATIDs für den Projektbereich zu bestimmen, ruft der Projektuntertyp die oben genannten Eigenschaften für [VSITEMID ab. Root](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>) aus `VSITEMID typedef`der . Ein Projektuntertyp kann auch **Property Pages** steuern, welche Eigenschaftenseiten-Dialogfeldseiten für das Projekt angezeigt werden, sowohl konfigurationsabhängig als auch konfigurationsunabhängig. Einige Projektuntertypen müssen möglicherweise integrierte Seiten entfernen und Projektuntertyp-spezifische Seiten hinzufügen. Um dies zu aktivieren, ruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> das verwaltete Clientprojekt die Methode für die folgenden Eigenschaften auf:

- `VSHPROPID_PropertyPagesCLSIDList`— eine durch Semikolons getrennte Liste von CLSIDs konfigurationsunabhängiger Eigenschaftenseiten.

- `VSHPROPID_CfgPropertyPagesCLSIDList —`eine durch Semikolons getrennte Liste von CLSIDs von konfigurationsabhängigen Eigenschaftenseiten.

Da der Projektuntertyp <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> das Objekt aggregiert, kann er die Definition dieser Eigenschaften überschreiben, um zu steuern, welche **Eigenschaftenseiten-Dialogfelder** angezeigt werden. Der Projektuntertyp kann diese Eigenschaften aus dem inneren Basisprojekt abrufen und dann bei Bedarf CLSIDs hinzufügen oder entfernen.

Neue Eigenschaftenseiten, die von einem Projektuntertyp hinzugefügt werden, erhalten ein Projektkonfigurationssuchobjekt aus der Basisprojektimplementierung. Dieses Projektkonfigurationssuchobjekt unterstützt Automation Extender. Weitere Informationen zu AutomationExtendern finden Sie unter [Implementieren und Verwenden von Automation Extendern](https://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356). Die Eigenschaftenseiten, die vom <xref:EnvDTE.Project.Extender%2A> Projektsubtype-Aufruf implementiert werden, um ihr eigenes Projekt-Subtype-Konfigurationssuchobjekt abzurufen, das das Konfigurationssuchobjekt des Basisprojekts erweitert.

## <a name="see-also"></a>Weitere Informationen

- <xref:EnvDTE.IFilterProperties>
- [Dialogfeld Eigenschaftenseiten](/previous-versions/visualstudio/visual-studio-2010/as5chysf(v=vs.100))
