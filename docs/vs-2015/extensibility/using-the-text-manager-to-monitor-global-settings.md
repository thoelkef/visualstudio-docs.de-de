---
title: Verwenden die Text-Manager zum Überwachen von globaler Einstellungen | Microsoft-Dokumentation
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
ms.openlocfilehash: 792c566eda53cb8a4703e8ab03982952c518d8e4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58956235"
---
# <a name="using-the-text-manager-to-monitor-global-settings"></a>Verwenden den Text-Manager zum Überwachen von globaler Einstellungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie einen Kern-Editor implementieren, müssen Sie die Änderungen, die an globale Einstellungen vorgenommen werden überwachen, da diese Änderungen auf Ihre Instanz des Editors auswirken können. Sie können die Änderungen verfolgen, durch Lauschen auf Ereignisse, die durch den TextManager ausgelöst. Beispielsweise, wenn Sie eine globale Einstellung für die Darstellung oder das Verhalten einer Komponente in der Kern-Editor, z. B. die dokumentendatenobjekt, angeben TextManager speichert diese Informationen und wird für alle betroffenen Clients kommuniziert.  
  
## <a name="text-manager-functions"></a>Text-Manager-Funktionen  
 Der Text-Manager löst Ereignisse für eine Reihe von Einstellungen, einschließlich der folgenden:  
  
- Gibt an, ob ein Puffer unter quellcodeverwaltung ist  
  
- Registrieren für Benachrichtigungen über datenbankänderungen-Datei  
  
- Gewusst wie: beibehalten Überblick darüber, welche Ansichten bestimmte Puffer zugeordnet sind.  
  
- Voreinstellungen für die farbliche Kennzeichnung von Text  
  
- Registerkarte im Vergleich zu den Einstellungen von Speicherplatz  
  
  Einstellungen, die für eine bestimmte Sprache eindeutig sind, werden nicht durch den TextManager verwaltet. Diese Einstellungen müssen von jeder Sprachdienst verwaltet werden.  
  
  Die ereignisbenachrichtigung für die Text-Manager erfolgt über die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents> Schnittstelle. Diese Schnittstelle implementieren, auf dem Client-Objekt zum Behandeln von Ereignissen ausgelöst TextManager. Registrieren Sie sich für diese Ereignisse mithilfe der <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> Schnittstelle für den TextManager.  
  
## <a name="see-also"></a>Siehe auch  
 [In der Kern-Editor](../extensibility/inside-the-core-editor.md)   
 [Editor-Funktionen](http://msdn.microsoft.com/bdac940d-1f14-4019-a01f-fd0bb3dc7198)
