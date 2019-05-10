---
title: Zugriff wird verweigert. | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 8a512060-d744-47af-a83e-4ba42ea2c5b2
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 9563cafa4895f89253b4073d788240806a86fa2a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62561077"
---
# <a name="access-is-denied"></a>Zugriff verweigert
Ein Skript hat versucht, auf Daten aus einer anderen Quelle als dem Host der aktuellen Seite zuzugreifen. Mit der Richtlinieneinschränkung der gleichen Quelle gefolgt vom Internet Explorer und anderen Browsern können Skripts nur auf Daten aus Quellen mit demselben Schema, Host und Port der URL der aktuellen Seite zugreifen.  
  
 Wenn die aktuelle Seite ist z. B. `https://employees.mycompany.com`, Sie können nicht auf Daten aus den folgenden URLs zugreifen:  
  
- `http://data.contoso.com`, da HTTP statt HTTPS verwendet wird.  
  
- `https://somedatasource.com`, da es sich um eine andere Domäne handelt.  
  
- `https://employees.mycompany.com:8888`, da es sich um einen anderen Port verwendet.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Überprüfen Sie, ob die API, die Sie aufrufen möchten, JSONP oder CORS unterstützt, d. h. zwei Ansätze, die Cross-Origin-Skripting sicher zulassen.  
  
- Wenn Sie versuchen, eine REST-API aufzurufen, gestalten Sie diesen Aufruf für Ihren serverseitigen Code um, und machen Sie dann den neuen REST-Endpunkt für Ihre clientseitigen Skripts verfügbar.  
  
     Weitere Informationen im Zusammenhang mit den Richtlinieneinschränkungen der gleichen Quelle, JSONP und CORS finden Sie in der Onlinedokumentation.
