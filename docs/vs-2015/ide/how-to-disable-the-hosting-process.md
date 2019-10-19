---
title: 'Vorgehensweise: Deaktivieren des Hostprozesses | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- hosting process, disabling
- vshost.exe, disabling the hosting process
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 95dcd7da113bfe996d00e617b7c8e2f9b68864d7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667971"
---
# <a name="how-to-disable-the-hosting-process"></a>Gewusst wie: Deaktivieren des Hostprozesses
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aufrufe an bestimmte APIs können beeinflusst werden, wenn der Hostprozesses aktiviert wird. In diesen Fällen ist es erforderlich, den Hostprozess zu deaktivieren, damit korrekte Ergebnisse zurückgegeben werden.

### <a name="to-disable-the-hosting-process"></a>So deaktivieren Sie den Hostprozess

1. Öffnen Sie ein ausführbares Projekt in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Projekte, die keine ausführbare Dateien erzeugen (z. B. Klassenbibliothek- oder Dienstprojekte) verfügen über diese Option nicht.

2. Klicken Sie im Menü **Projekt** auf **Eigenschaften**.

3. Klicken Sie auf die Registerkarte **Debuggen**.

4. Deaktivieren Sie das Kontrollkästchen **Visual Studio-Hostprozess aktivieren**.

   Wenn der Hostprozess deaktiviert ist, sind mehrere Debugfeatures nicht verfügbar oder weisen eine eingeschränkte Leistung auf. Weitere Informationen finden Sie unter [Debuggen und der Hostprozess](../debugger/debugging-and-the-hosting-process.md).

   Generelle Einschränkungen bei deaktiviertem Hostprozess:

- Die Vorlaufzeit bis zum Start des Debugvorgangs bei [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Anwendungen verlängert sich.

- Die Ausdrucksauswertung zur Entwurfszeit ist nicht verfügbar.

- Das Debuggen teilweise vertrauenswürdiger Anwendungen ist nicht möglich.

## <a name="see-also"></a>Siehe auch
 [Debuggen und](../debugger/debugging-and-the-hosting-process.md) Hostingprozess- [Hostingprozess (vshost. exe)](../ide/hosting-process-vshost-exe.md) [während der Anwendungsentwicklung](https://msdn.microsoft.com/c9497d62-3b7b-4449-88e8-cf27acc9efe6)
