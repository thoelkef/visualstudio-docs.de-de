---
title: 'Vorgehensweise: Hinzufügen von Standard Text Markierungen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - standard text markers
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 912d5d7a225520fc825d832bf73f5cfc733a9486
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840845"
---
# <a name="how-to-add-standard-text-markers"></a>Vorgehensweise: Hinzufügen von Standardtextmarkierungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verwenden Sie das folgende Verfahren, um einen der standardmäßigen Text Markertypen zu erstellen, die mit dem Kern Editor bereitgestellt werden [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
### <a name="to-create-a-text-marker"></a>So erstellen Sie einen Textmarker  
  
1. Abhängig davon, ob Sie ein ein-oder zweidimensionales Koordinatensystem verwenden, rufen Sie die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> Methode oder die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> Methode auf, um einen neuen Textmarker zu erstellen.  
  
     Geben Sie in diesem Methoden aufrufyp einen Markertyp, einen Textbereich, über den der Marker erstellt werden soll, und eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> Schnittstelle an. Diese Methode gibt dann einen Zeiger auf den neu erstellten Textmarker zurück. Markertypen werden aus der- <xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE> Enumeration entnommen. Geben <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> Sie eine Schnittstelle an, wenn Sie über markerereignisse informiert werden möchten.  
  
    > [!NOTE]
    > Erstellen Sie Textmarker nur auf dem Hauptbenutzer Oberflächen-Thread. Der Core-Editor basiert auf dem Inhalt des Text Puffers, um Textmarker zu erstellen, und der Text Puffer ist nicht Thread sicher.  
  
## <a name="adding-a-custom-command"></a>Hinzufügen eines benutzerdefinierten Befehls  
 Das Implementieren der `IVsTextMarkerClient` -Schnittstelle und das Bereitstellen eines Zeigers von einem Marker aus erweitert das markerverhalten auf verschiedene Weise. Zuerst können Sie Tipps für Ihren Marker bereitstellen und Befehle ausführen. Dies ermöglicht Ihnen außerdem das Empfangen von Ereignis Benachrichtigungen für einzelne Marker und das Erstellen eines benutzerdefinierten Kontextmenüs über den Marker. Verwenden Sie das folgende Verfahren, um dem markerkontextemenü einen benutzerdefinierten Befehl hinzuzufügen.  
  
#### <a name="to-add-a-custom-command-to-the-context-menu"></a>So fügen Sie dem Kontextmenü einen benutzerdefinierten Befehl hinzu  
  
1. Bevor das Kontextmenü angezeigt wird, ruft die Umgebung die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A> -Methode auf und übergibt Ihnen einen Zeiger auf den betroffenen Textmarker und die Nummer des Befehls Elements im Kontextmenü.  
  
     Beispielsweise enthalten die breakpointspezifischen Befehle im Kontextmenü den halte **Punkt entfernen** über den **neuen Haltepunkt**, wie im folgenden Screenshot dargestellt.  
  
     ![Marker-Kontextmenü](../extensibility/media/vsmarkercontextmenu.gif "vsmarkercontextmenu")  
  
2. Übergeben Sie Text zurück, der den Namen des benutzerdefinierten Befehls identifiziert. Beispielsweise könnte **Remove Breakpoint** ein benutzerdefinierter Befehl sein, wenn Sie von der Umgebung nicht bereits bereitgestellt wurde. Außerdem geben Sie zurück, ob der Befehl unterstützt, verfügbar und aktiviert ist und/oder ein ein-/ausschalten. Die Umgebung verwendet diese Informationen, um den benutzerdefinierten Befehl im Kontextmenü auf die richtige Weise anzuzeigen.  
  
3. Um den Befehl auszuführen, ruft die Umgebung die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> -Methode auf und übergibt Ihnen einen Zeiger auf den Textmarker und die Nummer des Befehls, der im Kontextmenü ausgewählt wird.  
  
     Verwenden Sie diese Informationen aus diesem-Befehl, um die Aktionen der Textmarkierung auszuführen, die Ihr benutzerdefinierter Befehl vorgibt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden von Text Markern mit der Legacy-API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Gewusst wie: Implementieren von Fehlermarkierungen](../extensibility/how-to-implement-error-markers.md)   
 [Gewusst wie: Erstellen von benutzerdefinierten Text Markern](../extensibility/how-to-create-custom-text-markers.md)   
 [Vorgehensweise: Verwenden von Textmarkierungen](../extensibility/how-to-use-text-markers.md)
