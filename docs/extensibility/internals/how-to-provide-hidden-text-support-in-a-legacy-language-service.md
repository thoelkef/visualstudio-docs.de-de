---
title: "Gewusst wie: unterst&#252;tzen ausgeblendeter Text in einem Legacy-Sprachdienst | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ausgeblendeter Text, Unterstützung"
  - "Editoren [Visual Studio SDK], ausgeblendeten text"
  - "Language Services, ausgeblendeten Text Regionen implementieren"
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# Gewusst wie: unterst&#252;tzen ausgeblendeter Text in einem Legacy-Sprachdienst
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Sie können Bereiche des ausgeblendeten Textes zusätzlich zu den Bereichen Kontur erstellen.  Bereiche des ausgeblendeten Textes können CLIENT\-gesteuert oder einem Editor und gesteuert werden verwendet, um einen Textbereich vollständig ausblenden.  Der Editor zeigt einen verborgenen Bereich als horizontale Linien an.  Ein Beispiel hierfür ist die Nur Skript\-Ansicht im HTML\-Editor.  
  
## Verfahren  
  
#### Um einen Bereich des ausgeblendeten Textes implementieren  
  
1.  Aufruf `QueryService` für <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>.  
  
     Dies gibt einen Zeiger auf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>zurück.  
  
2.  Rufen Sie das <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>an und einen Zeiger für einen angegebenen Textpuffer übergeben.  Dadurch wird bestimmt, ob eine Sitzung des ausgeblendeten Textes bereits für den Puffer vorhanden ist.  
  
3.  Wenn ein bereits vorhanden ist, dann ist es nicht erforderlich, um ein zu erstellen und einen Zeiger auf den vorhandenen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>\-Objekt wird zurückgegeben.  Verwenden Sie diesen Zeiger, um Bereiche des ausgeblendeten Textes aufzulisten und zu erstellen.  Andernfalls Aufrufs <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> , um eine Sitzung des ausgeblendeten Textes für den Puffer zu erstellen.  
  
     Ein Zeiger auf den <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>\-Objekt wird zurückgegeben.  
  
    > [!NOTE]
    >  Wenn Sie `CreateHiddenTextSession`aufrufen, können Sie einen Client des ausgeblendeten Textes \(d. h. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>\) angeben.  Der Client des ausgeblendeten Textes benachrichtigt Sie, ob ausgeblendeter Text oder Gliederung vom Benutzer erweitert oder reduziert wird.  
  
4.  Rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> auf, um eine oder mehrere neue Bereiche Kontur jeweils die folgenden Informationen hinzuzufügen und `reHidReg` im Parameter \(<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>\) angeben:  
  
    1.  Geben Sie einen Wert `hrtConcealed` im `iType`\-Member der <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> Struktur an, dass Sie einen verborgenen Bereich erstellen, anstatt Gliederung im Bereich angeben.  
  
        > [!NOTE]
        >  Wenn sie verborgen sind, werden die Bereiche Zeilen des Editors wird automatisch um die ausgeblendeten Bereiche ausgeblendet, um ihr Vorhandensein anzugeben.  
  
    2.  Geben Sie an, ob der Bereich CLIENT\-gesteuert oder `dwBehavior`\-Member der <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> Struktur aus einem Editor gesteuert wird.  Die intelligente Implementierung Gliedern kann eine Kombination aus CLIENT\-gesteuerten Konturen\- und Bereichen des Herausgebers und Text enthalten.