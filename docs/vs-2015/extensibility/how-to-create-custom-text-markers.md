---
title: 'Gewusst wie: Erstellen von benutzerdefinierten Text Markern | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - custom text markers
ms.assetid: 6e32ed81-c604-4a32-9012-8db3bec7c846
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ac681879e0f7ad0902358be23d74d57ccee406f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840851"
---
# <a name="how-to-create-custom-text-markers"></a>Vorgehensweise: Erstellen von benutzerdefinierten Diagrammen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie einen benutzerdefinierten Textmarker zum hervorheben oder organisieren von Code erstellen möchten, müssen Sie die folgenden Schritte ausführen:  
  
- Registrieren Sie den neuen Textmarker, damit andere Tools darauf zugreifen können.  
  
- Bereitstellen einer Standard Implementierung und Konfiguration des Text Markers  
  
- Erstellen Sie einen Dienst, der von anderen Prozessen verwendet werden kann, um den Textmarker zu verwenden.  
  
  Ausführliche Informationen zum Anwenden eines Text Markers auf einen Code Bereich finden Sie unter Gewusst [wie: Verwenden von Text Markern](../extensibility/how-to-use-text-markers.md).  
  
### <a name="to-register-a-custom-marker"></a>So registrieren Sie einen benutzerdefinierten Marker  
  
1. Erstellen Sie einen Registrierungs Eintrag wie folgt:  
  
    HKEY_LOCAL_MACHINE \software\microsoft\visualstudio \\ *\<Version>* \text Editor \ externe Marker\\*\<MarkerGUID>*  
  
    <em>\<MarkerGUID></em>ist eine `GUID` , die zum Identifizieren des hinzugefügten Markers verwendet wird.  
  
    *\<Version>* ist die Version von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , z. b. 8,0  
  
    *\<PackageGUID>* die GUID des VSPackage, das das Automatisierungs Objekt implementiert.  
  
   > [!NOTE]
   > Der Stammpfad von HKEY_LOCAL_MACHINE \software\microsoft\visualstudio \\ *\<Version>* kann beim Initialisieren der Visual Studio-Shell mit einem alternativen Stamm überschrieben werden. Weitere Informationen finden Sie unter [Befehls Zeilenschalter](../extensibility/command-line-switches-visual-studio-sdk.md).  
  
2. Erstellen Sie unter HKEY_LOCAL_MACHINE \software\microsoft\visualstudio \\ *\<Version>* \text Editor \ externe Marker vier Werte.\\*\<MarkerGUID>*  
  
   - (Standardwert)  
  
   - Dienst  
  
   - DisplayName  
  
   - Paket  
  
   - `Default` ist ein optionaler Eintrag vom Typ REG_SZ. Wenn festgelegt, ist der Wert des Eintrags eine Zeichenfolge, die einige nützliche identifizierende Informationen enthält, z. b. "benutzerdefinierter Text Marker".  
  
   - `Service` ein Eintrag vom Typ REG_SZ mit der GUID-Zeichenfolge des Dienstanbieter, der die benutzerdefinierte Textmarkierung bereitstellt <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> . Das Format ist {xxxxxx xxxx xxxx xxxx xxxxxxxxx}.  
  
   - `DisplayName` ein Eintrag vom Typ REG_SZ, der die Ressourcen-ID des Namens der benutzerdefinierten Textmarkierung enthält. Das Format ist #YYYY.  
  
   - `Package` ist ein Eintrag vom Typ REG_SZ der das `GUID` VSPackage enthält, das den unter Dienst aufgelisteten Dienst bereitstellt. Das Format ist {xxxxxx xxxx xxxx xxxx xxxxxxxxx}.  
  
### <a name="to-create-a-custom-text-marker"></a>So erstellen Sie einen benutzerdefinierten Textmarker  
  
1. Implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>-Schnittstelle.  
  
     Die Implementierung dieser Schnittstelle definiert das Verhalten und die Darstellung des benutzerdefinierten Markertyps.  
  
     Diese Schnittstelle wird aufgerufen, wenn  
  
    1. Ein Benutzer startet die IDE zum ersten Mal.  
  
    2. Ein Benutzer wählt die Schaltfläche **Standardwerte zurücksetzen** auf der Eigenschaften Seite **Schriftarten und Farben** im Ordner **Umgebung** aus, die sich im linken Bereich des Dialog Felds **Optionen** befindet **, das über das Menü Extras** der IDE abgerufen wird.  
  
2. Implementieren Sie die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A> Methode, und geben Sie an, welche `IVsPackageDefinedTextMarkerType` Implementierung basierend auf der Markertyp-GUID zurückgegeben werden soll.  
  
     Die Umgebung ruft diese Methode bei der erstmaligen Erstellung des benutzerdefinierten Markertyps auf und gibt eine GUID an, die den benutzerdefinierten Markertyp identifiziert.  
  
### <a name="to-proffer-your-marker-type-as-a-service"></a>So profferdu deinen Markertyp als Dienst  
  
1. Ruft die- <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A> Methode für auf <xref:Microsoft.VisualStudio.Shell.Interop.SProfferService> .  
  
     Ein Zeiger auf <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> wird zurückgegeben.  
  
2. Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A> -Methode auf und gibt die GUID an, die den benutzerdefinierten markertypdienst identifiziert und einen Zeiger auf die Implementierung der- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> Schnittstelle bereitstellt. Ihre <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> Implementierung sollte einen Zeiger auf Ihre Implementierung der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> Schnittstelle zurückgeben.  
  
     Ein eindeutiges Cookie, das identifiziert, dass Ihr Dienst zurückgegeben wird. Sie können dieses Cookie später verwenden, um den benutzerdefinierten Markertyp Dienst zu widerrufen, indem Sie die- <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> Methode der- <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> Schnittstelle aufrufen  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden von Text Markern mit der Legacy-API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Vorgehensweise: Hinzufügen von Standard Text Markern](../extensibility/how-to-add-standard-text-markers.md)   
 [Gewusst wie: Implementieren von Fehlermarkierungen](../extensibility/how-to-implement-error-markers.md)   
 [Vorgehensweise: Verwenden von Textmarkierungen](../extensibility/how-to-use-text-markers.md)
