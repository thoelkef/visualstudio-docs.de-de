---
title: Die Verbindungs Eigenschaft in der Datei mit den Anwendungseinstellungen fehlt oder ist falsch. | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 77724510-ff59-4d43-b933-a0434e1ac597
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b51ff1b20f197de5b6773413558b7e71764780b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655402"
---
# <a name="the-connection-property-in-the-application-settings-file-is-missing-or-incorrect"></a>Die Verbindungseigenschaft in der Application Settings-Datei fehlt oder ist fehlerhaft.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Verbindungseigenschaft fehlt in der Datei mit den Anwendungseinstellungen, oder sie ist falsch. Stattdessen wurde die Verbindungszeichenfolge aus der DBML-Datei verwendet.

 Die DBML-Datei enthält einen Verweis auf eine Verbindungszeichenfolge in der Datei mit den Anwendungseinstellungen, die nicht gefunden wurde. Diese Meldung dient zu Informationszwecken. Die Einstellung für die Verbindungszeichenfolge wird erstellt, wenn auf **OK** geklickt wird.

### <a name="to-respond-to-this-message"></a>So reagieren Sie auf diese Meldung

- Klicken Sie auf **OK**. Die Verbindungsinformationen, die in der DBML-Datei enthalten sind, werden den Anwendungseinstellungen hinzugefügt.

## <a name="see-also"></a>Weitere Informationen
 [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) Exemplarische Vorgehensweise [: Erstellen von LINQ to SQL Klassen (O-R-Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [NIB: Gewusst wie: Hinzufügen oder Entfernen von Anwendungseinstellungen](https://msdn.microsoft.com/a233965c-126d-46ab-add4-efb758f576f4) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
