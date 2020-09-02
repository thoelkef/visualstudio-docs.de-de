---
title: 'Gewusst wie: Verwenden von GetGlobalService | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- services, GetGlobalService
ms.assetid: 4cdf5ab5-9f09-4caf-9011-2dcb2c62f1b7
caps.latest.revision: 14
manager: jillfra
ms.openlocfilehash: 1c1fb48e4bb354ef403b39b0f1320ead92f43967
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62948181"
---
# <a name="how-to-use-getglobalservice"></a>Gewusst wie: Verwenden von GetGlobalService
Manchmal müssen Sie möglicherweise einen Dienst von einem Tool Fenster oder einem Steuerelement Container erhalten, der nicht mit der sitsierung vertraut ist, oder wenn Sie mit einem Dienstanbieter vertraut sind, der den gewünschten Dienst nicht kennt. Beispielsweise können Sie in einem-Steuerelement in das Aktivitätsprotokoll schreiben. Weitere Informationen zu diesen und anderen Szenarien finden Sie unter Gewusst [wie:](../extensibility/how-to-troubleshoot-services.md)Problembehandlung bei Diensten.  
  
 Sie können die meisten [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Dienste abrufen, indem Sie die statische- <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> Methode aufrufen.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> basiert auf einem zwischengespeicherten Dienstanbieter, der initialisiert wird, wenn ein VSPackage, das von abgeleitet wird, das erste Mal <xref:Microsoft.VisualStudio.Shell.Package> ist. Sie müssen sicherstellen, dass diese Bedingung erfüllt ist, oder Sie müssen auf einen NULL-Dienst vorbereitet werden.  
  
 Glücklicherweise <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> funktioniert meistens ordnungsgemäß.  
  
- Wenn ein VSPackage einen Dienst bereitstellt, der nur einem anderen VSPackage bekannt ist, wird das VSPackage, das den Dienst anfordert, positioniert, bevor das VSPackage, das den Dienst bereitstellt, geladen wird.  
  
- Wenn ein Tool Fenster durch ein VSPackage erstellt wird, wird das VSPackage vor dem Erstellen des Tool Fensters positioniert.  
  
- Wenn ein Steuerelement Container von einem Tool Fenster gehostet wird, das von einem VSPackage erstellt wurde, wird das VSPackage vor dem Erstellen des Steuerelement Containers positioniert.  
  
### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>So erhalten Sie einen Dienst in einem Tool Fenster oder Steuerelement Container  
  
- Fügen Sie diesen Code in den Konstruktor, das Tool Fenster oder den Steuerelement Container ein:  
  
     [!code-csharp[UseGetGlobalService#1](../snippets/csharp/VS_Snippets_VSSDK/usegetglobalservice/cs/getglobalservicepackage.cs#1)]
     [!code-vb[UseGetGlobalService#1](../snippets/visualbasic/VS_Snippets_VSSDK/usegetglobalservice/vb/getglobalservicepackage.vb#1)]  
  
     Mit diesem Code wird ein SVsActivityLog-Dienst abgerufen und in eine- <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> Schnittstelle umgewandelt, die zum Schreiben in das Aktivitätsprotokoll verwendet werden kann. Ein Beispiel finden Sie unter Gewusst [wie: Verwenden des Aktivitäts Protokolls](../extensibility/how-to-use-the-activity-log.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vorgehensweise: Problembehandlung bei Diensten](../extensibility/how-to-troubleshoot-services.md)   
 [Verwenden von und Bereitstellen von Diensten](../extensibility/using-and-providing-services.md)   
 [Dienstgrundlagen](../extensibility/internals/service-essentials.md)