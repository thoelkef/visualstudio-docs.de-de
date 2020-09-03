---
title: Zugriff verweigert | Microsoft-Dokumentation
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 8a512060-d744-47af-a83e-4ba42ea2c5b2
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 874f7c0e5dcfaf4881c059a77f1c5e930d8c0578
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85814836"
---
# <a name="access-is-denied"></a>Zugriff verweigert
Ein Skript hat versucht, auf Daten aus einer anderen Quelle als dem Host der aktuellen Seite zuzugreifen. Mit der Richtlinieneinschränkung der gleichen Quelle gefolgt vom Internet Explorer und anderen Browsern können Skripts nur auf Daten aus Quellen mit demselben Schema, Host und Port der URL der aktuellen Seite zugreifen.  
  
 Wenn die aktuelle Seite z. b. lautet `https://employees.mycompany.com` , können Sie nicht auf die Daten der folgenden URLs zugreifen:  
  
- `http://data.contoso.com`, weil HTTP anstelle von HTTPS verwendet wird.  
  
- `https://somedatasource.com`, da es sich um eine andere Domäne handelt.  
  
- `https://employees.mycompany.com:8888`, weil ein anderer Port verwendet wird.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Überprüfen Sie, ob die API, die Sie aufrufen möchten, JSONP oder CORS unterstützt, d. h. zwei Ansätze, die Cross-Origin-Skripting sicher zulassen.  
  
- Wenn Sie versuchen, eine REST-API aufzurufen, gestalten Sie diesen Aufruf für Ihren serverseitigen Code um, und machen Sie dann den neuen REST-Endpunkt für Ihre clientseitigen Skripts verfügbar.  
  
     Weitere Informationen im Zusammenhang mit den Richtlinieneinschränkungen der gleichen Quelle, JSONP und CORS finden Sie in der Onlinedokumentation.
