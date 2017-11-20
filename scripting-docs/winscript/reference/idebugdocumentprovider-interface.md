---
title: IDebugDocumentProvider-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugDocumentProvider interface
ms.assetid: 36510acf-1ef9-479c-a430-d3f09502f82c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 262794718e238068cfd9a8e3fae5161b9fe8cc54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumentprovider-interface"></a>IDebugDocumentProvider-Schnittstelle
Bietet die Möglichkeit zum Instanziieren eines Dokuments nach Bedarf.  
  
## <a name="remarks"></a>Hinweise  
 Das indirekte bedeutet, dass zum Instanziieren eines Dokuments:  
  
-   Ermöglicht das Dokument geladen werden, wenn er benötigt wird.  
  
-   Ermöglicht das Document-Objekt innerhalb des Debuggers IDE enthalten sein soll.  
  
-   Können mehrere Möglichkeiten, auf das gleichen Dokumentobjekt zuzugreifen.  
  
 Dadurch effektiv trennt das Dokument, von dem Anbieter und den Anbieter Zusatzinformationen zur Laufzeit Kontext durchführen.  
  
 Zusätzlich zu den von geerbten Methoden `IDebugDocumentInfo`, `IDebugDocumentProvider` Schnittstelle macht die folgenden Methoden verfügbar.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugDocumentProvider::GetDocument](../../winscript/reference/idebugdocumentprovider-getdocument.md)|Bewirkt, dass das Dokument instanziiert werden, wenn sie nicht bereits vorhanden ist.|