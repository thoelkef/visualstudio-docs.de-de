---
title: Verwenden die Text-Manager zum Überwachen von globaler Einstellungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - monitor global settings
- editors [Visual Studio SDK], legacy - text manager
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d0378d4c8c021cb47362220b49c8d7cb5a4ebc82
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079786"
---
# <a name="use-the-text-manager-to-monitor-global-settings"></a>Verwenden Sie den TextManager zum Überwachen von globaler Einstellungen
Wenn Sie einen Kern-Editor implementieren, müssen Sie die Änderungen, die an globale Einstellungen vorgenommen werden überwachen, da diese Änderungen auf Ihre Instanz des Editors auswirken können. Sie können die Änderungen verfolgen, durch Lauschen auf Ereignisse, die durch den TextManager ausgelöst. Beispielsweise, wenn Sie eine globale Einstellung für die Darstellung oder das Verhalten einer Komponente in der Kern-Editor, z. B. die dokumentendatenobjekt, angeben TextManager speichert diese Informationen und wird für alle betroffenen Clients kommuniziert.  
  
## <a name="text-manager-functions"></a>Text-Manager-Funktionen  
 Der Text-Manager löst Ereignisse für eine Reihe von Einstellungen, einschließlich der folgenden:  
  
-   Gibt an, ob ein Puffer unter quellcodeverwaltung ist  
  
-   Registrieren für Benachrichtigungen über datenbankänderungen-Datei  
  
-   Gewusst wie: beibehalten Überblick darüber, welche Ansichten bestimmte Puffer zugeordnet sind.  
  
-   Voreinstellungen für die farbliche Kennzeichnung von Text  
  
-   Registerkarte im Vergleich zu den Einstellungen von Speicherplatz  
  
 Einstellungen, die für eine bestimmte Sprache eindeutig sind, werden nicht durch den TextManager verwaltet. Diese Einstellungen müssen von jeder Sprachdienst verwaltet werden.  
  
 Die ereignisbenachrichtigung für die Text-Manager erfolgt über die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents> Schnittstelle. Diese Schnittstelle implementieren, auf dem Client-Objekt zum Behandeln von Ereignissen ausgelöst TextManager. Registrieren Sie sich für diese Ereignisse mithilfe der <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> Schnittstelle für den TextManager.  
  
## <a name="see-also"></a>Siehe auch  
 [In der Kern-editor](../extensibility/inside-the-core-editor.md)   
 [Editor-Funktionen](http://msdn.microsoft.com/en-us/bdac940d-1f14-4019-a01f-fd0bb3dc7198)