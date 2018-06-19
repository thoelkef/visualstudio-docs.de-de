---
title: 'Vorgehensweise: Deaktivieren des Hostprozesses'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- hosting process, disabling
- vshost.exe, disabling the hosting process
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f7970ff97c7aec42f8798da07cf2a4a2b6c8bea8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31942060"
---
# <a name="how-to-disable-the-hosting-process"></a>Vorgehensweise: Deaktivieren des Hostprozesses

Aufrufe an bestimmte APIs können beeinflusst werden, wenn der Hostprozesses aktiviert wird. In diesen Fällen ist es erforderlich, den Hostprozess zu deaktivieren, damit korrekte Ergebnisse zurückgegeben werden.

## <a name="to-disable-the-hosting-process"></a>So deaktivieren Sie den Hostprozess

1.  Öffnen Sie ein ausführbares Projekt in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Projekte, die keine ausführbare Dateien erzeugen (z. B. Klassenbibliothek- oder Dienstprojekte) verfügen über diese Option nicht.

2.  Klicken Sie im Menü **Projekt** auf **Eigenschaften**.

3.  Klicken Sie auf die Registerkarte **Debuggen**.

4.  Deaktivieren Sie das Kontrollkästchen **Visual Studio-Hostprozess aktivieren**.

 Wenn der Hostprozess deaktiviert ist, sind mehrere Debugfunktionen nicht verfügbar oder weisen eine eingeschränkte Leistung auf. Weitere Informationen finden Sie unter [Debuggen und der Hostprozess](../debugger/debugging-and-the-hosting-process.md).

 Generelle Einschränkungen bei deaktiviertem Hostprozess:

-   Die Vorlaufzeit bis zum Start des Debugvorgangs bei [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]-Anwendungen verlängert sich.

-   Die Ausdrucksauswertung zur Entwurfszeit ist nicht verfügbar.

-   Das Debuggen teilweise vertrauenswürdiger Anwendungen ist nicht möglich.

## <a name="see-also"></a>Siehe auch

- [Debuggen und der Hostprozess](../debugger/debugging-and-the-hosting-process.md)
- [Hostprozess (vshost.exe)](../ide/hosting-process-vshost-exe.md)