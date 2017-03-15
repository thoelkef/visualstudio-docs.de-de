---
title: "Gewusst wie: Aktualisieren der Statusleiste | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] legacy - aktualisieren Statusleiste"
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Gewusst wie: Aktualisieren der Statusleiste
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**Statusleiste** ist eine Steuerleiste, die am unteren Rand viele Anwendungsfenster befindet, die eine oder mehrere Status textzeilen oder \- Leistungsindikatoren enthält.  
  
### So aktualisieren Sie die Statusleiste  
  
1.  Implementieren Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> für jedes einzelne Ansichtsobjekt \(DocView\) dass der Editor bereitstellt, z. B. eine Formularansicht und der Codeansicht.  
  
2.  Wenn die IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>aufruft, aktualisieren Sie die Informationen in **Statusleiste** , indem Sie die Methoden von <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>aufrufen.  
  
    > [!NOTE]
    >  Die IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> wird nur angezeigt, wenn das Dokumentfenster zum ersten Mal aktiviert wird.  Für den Rest der Zeit, als das Dokumentfenster aktiv ist, müssen Sie die **Statusleiste** Informationen aktualisieren, während sich der Zustand des Editors geändert wird.  
  
## Robuste Programmierung  
 **Statusleiste** enthält vier verschiedene Felder:  
  
-   Statustext  
  
-   Statusanzeige  
  
-   Animiertes Symbol  
  
-   Informationen zum Editor  
  
 Weitere Informationen finden Sie unter [Statusleisten](/visual-cpp/mfc/status-bars).  
  
 Die IDE ruft automatisch die <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>\-Methode der <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> Implementierung an, wenn das Dokumentfenster aktiviert ist.  
  
 Die VSPackage\-Implementierung ist für die Aktualisierung des Status Linktext in der Statusleiste verantwortlich.  Die IDE fügt diese Zeichenfolge „VORBEREITET“ zurück, wenn das Textfeld Status festgelegt wurde, dass Text \(""\) an der Leerlaufzeit zu leeren.  
  
## Siehe auch  
 [Statusleisten](/visual-cpp/mfc/status-bars)