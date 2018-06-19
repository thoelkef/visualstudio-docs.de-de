---
title: 'Vorgehensweise: Erstellen von benutzerdefinierten Text Marker | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - custom text markers
ms.assetid: 6e32ed81-c604-4a32-9012-8db3bec7c846
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f5c44a507cc291b203fc9ba330b248a854f61b81
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132262"
---
# <a name="how-to-create-custom-text-markers"></a>Vorgehensweise: Erstellen von benutzerdefinierten Text-Marker
Wenn Sie einen benutzerdefinierten Text Marker zum Hervorheben oder Organisieren von Code erstellen möchten, müssen Sie die folgenden Schritte ausführen:  
  
-   Registrieren Sie den neuen Text Marker, sodass andere Tools, die darauf zugreifen können  
  
-   Geben Sie einen Standardimplementierung und Konfiguration des Markers aus text  
  
-   Erstellen ein Diensts, der von anderen Prozessen verwendet werden kann, zu der Markierung Text verwenden  
  
 Details dazu, wie Sie einen Text-Marker für einen Codebereich gelten, finden Sie unter [Vorgehensweise: verwenden Text Marker](../extensibility/how-to-use-text-markers.md).  
  
### <a name="to-register-a-custom-marker"></a>Um eine benutzerdefinierte Markierung zu registrieren.  
  
1.  Erstellen Sie einen Registrierungseintrag wie folgt:  
  
     HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<Version >* \Text Editor\External Marker\\*\<MarkerGUID >*  
  
     *\<MarkerGUID >* ist eine `GUID` zur Identifizierung der Markierung hinzugefügt wird  
  
     *\<Version >* ist die Version des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], z. B. 8.0  
  
     *\<PackageGUID >* ist die GUID des VSPackage das Automatisierungsobjekt implementieren.  
  
    > [!NOTE]
    >  Der Stammpfad des HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<Version >* kann mit einem anderen Stamm überschrieben werden, wenn die Visual Studio-Shell, müssen Sie weitere Informationen finden Sie unter initialisiert wird [Befehlszeilenschalter](../extensibility/command-line-switches-visual-studio-sdk.md).  
  
2.  Erstellen Sie die vier Werte unter HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<Version >* \Text Editor\External Marker\\*\<MarkerGUID >*  
  
    -   (Standard)  
  
    -   Dienst  
  
    -   DisplayName  
  
    -   Package  
  
    -   `Default` ist ein optionaler Eintrag vom Typ REG_SZ. Wenn festgelegt ist, ist der Wert des Eintrags, eine Zeichenfolge, enthält hilfreiche identifizierende Informationen, z. B. "benutzerdefinierter Text Marker" auf.  
  
    -   `Service` ein Eintrag vom Typ REG_SZ ist, enthält die GUID-Zeichenfolge des Diensts, der den benutzerdefinierten Text Marker durch proffering bietet <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>. Das Format ist {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
    -   `DisplayName` ist die Ressourcen-ID, der den Namen der benutzerdefinierten Text Markierung, die ein Eintrag vom Typ REG_SZ enthält. Das Format ist #YYYY.  
  
    -   `Package` ist die Eingabe des Typs REG_SZ, enthält die `GUID` VSPackage, das vom Dienst aufgeführt, unter dem Dienst. Das Format ist {XXXXXX XXXX XXXX XXXX XXXXXXXXX}.  
  
### <a name="to-create-a-custom-text-marker"></a>So erstellen einen benutzerdefinierten Text-marker  
  
1.  Implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>-Schnittstelle.  
  
     Die Implementierung dieser Schnittstelle definiert das Verhalten und Aussehen Ihres benutzerdefinierten Marker-Typs.  
  
     Diese Schnittstelle wird aufgerufen  
  
    1.  Ein Benutzer startet die IDE zum ersten Mal an.  
  
    2.  Wählt ein Benutzer die **Standardwerte zurücksetzen** Schaltfläche unter der **Schriftarten und Farben** Eigenschaftenseite in der **Umgebung** Ordner im linken Bereich des der  **Optionen** Dialogfeld abgerufen, von der **Tools** Menü der IDE.  
  
2.  Implementieren der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A> Methode, die angeben, welche `IVsPackageDefinedTextMarkerType` Implementierung zurückgegeben werden soll basierend auf den Markertyp GUID, die im Aufruf Methode angegeben.  
  
     Die Umgebung ruft dieser Methode die erste Zeit Ihrer benutzerdefinierten Marker-Typ erstellt wird, und gibt eine GUID zur Kennzeichnung des benutzerdefinierten Marker-Typs.  
  
### <a name="to-proffer-your-marker-type-as-a-service"></a>Um Ihre Markertyp als Dienst proffer  
  
1.  Rufen Sie die <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A> Methode zum <xref:Microsoft.VisualStudio.Shell.Interop.SProfferService>.  
  
     Ein Zeiger auf <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> wird zurückgegeben.  
  
2.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A> Methode, dabei werden die GUID, die Ihren benutzerdefinierten Marker-Typ-Dienst erkennen und bereitstellen, einen Zeiger auf die Implementierung der <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> Schnittstelle. Ihre <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> Implementierung sollte einen Zeiger auf die Implementierung von zurück <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> Schnittstelle.  
  
     Ein eindeutiger Cookie identifiziert werden, wird Ihr Dienst zurückgegeben. Später können Sie dieses Cookie durch Aufrufen den benutzerdefinierten Marker-Typ-Dienst widerrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> Methode der <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> Schnittstelle, die die Angabe dieses Werts Cookie.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Text Marker mit der Legacy-API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Vorgehensweise: Hinzufügen von Standard-Text-Marker](../extensibility/how-to-add-standard-text-markers.md)   
 [Vorgehensweise: Implementieren von Fehler Marker](../extensibility/how-to-implement-error-markers.md)   
 [Vorgehensweise: Verwenden von Text-Marker](../extensibility/how-to-use-text-markers.md)