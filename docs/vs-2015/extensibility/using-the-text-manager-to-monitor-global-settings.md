---
title: Verwenden des Text-Managers zum Überwachen von globalen Einstellungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - monitor global settings
- editors [Visual Studio SDK], legacy - text manager
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ece51450b8344ae4715a912399ec538171a26a5c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695467"
---
# <a name="using-the-text-manager-to-monitor-global-settings"></a>Verwenden des Text-Managers zum Überwachen von globalen Einstellungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie einen Kern Editor implementieren, müssen Sie die an den globalen Einstellungen vorgenommenen Änderungen überwachen, da sich diese Änderungen auf die Instanz des Editors auswirken können. Sie können die Änderungen nachverfolgen, indem Sie Ereignisse überwachen, die vom Text-Manager ausgelöst werden. Wenn Sie z. b. eine globale Einstellung für die Darstellung oder das Verhalten einer Komponente im Kern-Editor angeben, z. b. das Dokument Datenobjekt, speichert der Text-Manager diese Informationen und kommuniziert sie an alle betroffenen Clients.  
  
## <a name="text-manager-functions"></a>Text-Manager-Funktionen  
 Der Text-Manager löst Ereignisse für eine Reihe von Einstellungen aus, einschließlich der folgenden:  
  
- Ob sich ein Puffer unter Quell Code Verwaltung befindet  
  
- Registrieren für Datei Änderungs Benachrichtigungen  
  
- Vorgehensweise beim Nachverfolgen, welche Sichten bestimmten Puffern zugeordnet sind  
  
- Einstellungen für die Farbgebung von Text  
  
- Registerkarten-und Speicherplatz Einstellungen  
  
  Voreinstellungen, die für eine bestimmte Sprache eindeutig sind, werden nicht vom Text-Manager verwaltet. Diese Einstellungen müssen von jedem Sprachdienst verwaltet werden.  
  
  Die Ereignis Benachrichtigung für den Text-Manager wird von der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents> Schnittstelle bereitgestellt. Implementieren Sie diese Schnittstelle für das Client Objekt, um Ereignisse zu behandeln, die den Text-Manager ausgelöst haben Sie registrieren sich für diese Ereignisse, indem Sie die- <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> Schnittstelle für den Text-Manager verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Im Kern-Editor](../extensibility/inside-the-core-editor.md)   
 [Editor-Funktionen](https://msdn.microsoft.com/bdac940d-1f14-4019-a01f-fd0bb3dc7198)
