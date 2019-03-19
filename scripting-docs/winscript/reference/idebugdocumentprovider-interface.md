---
title: IDebugDocumentProvider-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 5632134c86b5aa0e3cb769a68d2d4cfd944ff35c
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157209"
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