---
title: Die Richtlinie und des Eigenschaftenfensters | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 51735bf0f46e5a1ead6f989a8e75745ebc8e6e35
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="template-policy-and-the-properties-window"></a>Die Richtlinie und des Eigenschaftenfensters
Wenn ein Projekt in einem Enterprise-Vorlagen-Projekt enthalten ist, kann diese Enterprise-Vorlagenprojekt Richtlinie erzwingen. Die Richtlinie wird ein einschränkenden System, das zum Festlegen der Standardwerte für Eigenschaften, Eigenschaften ausblenden, Hinzufügen von Eigenschaften und usw. verwendet werden kann.  
  
 Verwenden die Richtlinie zum Steuern der Anzeige von Informationen in den **Eigenschaften** Fenster unterscheidet sich von der Implementierung <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>Objekteigenschaften auf der Komponentenebene, verarbeitet, während die Richtlinie verwendet werden kann, um Objekteigenschaften Ebene der Projektmappe oder das Projekt zu beschränken. Mit anderen Worten,  
  
-   Implementieren Sie die Methoden auf <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> bestimmen Sie die Anzeige auf die **Eigenschaften** Fenster für bestimmte Objekte  
  
-   Verwenden Sie die Richtlinie auf der Ebene Projektmappen- und Projektdateien, um zu bestimmen, der Anzeige auf die **Eigenschaften** Fenster für die zuvor angegebenen Objekte  
  
 Mit der Richtlinie, die um bestimmte Eigenschaften im selektiv zu beschränken die **Eigenschaften** Fenster beim Erstellen eines bestimmten Typs ein Projektelement ausgewählt ist **Projektmappen-Explorer** kann nützlich sein, alle Mitglieder der das Entwicklungsteam an einem Projekt arbeiten. Z. B. können mit der Richtlinie, Sie alle Verbindungszeichenfolgen-Informationen in einer Datenbank für Ihre Entwickler einrichten und Aktivieren des Schreibschutzes für der Verbindungszeichenfolge. Auf diese Weise können Sie angeben, dass eine einfache Möglichkeit, um sicherzustellen, dass jeder Entwickler den richtigen Pfad für den Datenzugriff verwendet.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md)