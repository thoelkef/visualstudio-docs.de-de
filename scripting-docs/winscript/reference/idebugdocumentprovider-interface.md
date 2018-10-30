---
title: IDebugDocumentProvider-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentProvider interface
ms.assetid: 36510acf-1ef9-479c-a430-d3f09502f82c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d775deb153205d0e9a452775272285c67e74a210
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949863"
---
# <a name="idebugdocumentprovider-interface"></a>IDebugDocumentProvider-Schnittstelle
Bietet die Möglichkeit zum Instanziieren eines Dokuments nach Bedarf.  
  
## <a name="remarks"></a>Hinweise  
 Das indirekte bedeutet zum Instanziieren eines Dokuments:  
  
- Ermöglicht das Dokument zu laden, wenn er benötigt wird.  
  
- Ermöglicht das Document-Objekt, in der Debugger-IDE enthalten sein sollen.  
  
- Können mehrere Möglichkeiten zum Zugriff auf das gleiche Dokumentobjekt.  
  
  Dadurch effektiv trennt das Dokument von dem Anbieter und den Anbieter um zusätzliche Kontextinformationen für Laufzeit durchzuführen.  
  
  Zusätzlich zu den von geerbten Methoden `IDebugDocumentInfo`, `IDebugDocumentProvider` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugDocumentProvider::GetDocument](../../winscript/reference/idebugdocumentprovider-getdocument.md)|Bewirkt, dass das Dokument instanziiert werden, wenn es nicht bereits vorhanden ist.|