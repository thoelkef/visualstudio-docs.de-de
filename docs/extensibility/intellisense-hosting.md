---
title: "Hosten von IntelliSense | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] legacy - IntelliSense-hosting"
ms.assetid: 20c61f8a-d32d-47e2-9c67-bf721e2cbead
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Hosten von IntelliSense
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio ermöglicht es IntelliSense\-Hosten.  IntellSense\-Hosting können Sie IntelliSense für Code bereitstellen, der nicht vom Visual Studio\-Text\-Editor gehostet wird.  
  
## IntelliSense, das dem hostet  
 In Visual Studio kann jeglicher Code, der Zugriff auf einen festgelegten Schließen und ein Textpuffer IntelliSense\-Fenster an einer beliebigen Stelle in der Benutzeroberfläche in erhalten.  Einige Beispiele sind dieses Szenarios Schließen im **Überwachen** Fenster oder im Feld Bedingung für Haltepunkt eines Fensters.  
  
### Implementierungs\-Schnittstellen  
  
#### IVsIntellisenseHost  
 Eine Benutzeroberflächenkomponente, der als Host für die IntelliSense\-Popupfenster <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>\-Schnittstelle unterstützen müssen.  Die standardmäßige Kern editor\-Text enthält eine vordefinierte Ansicht <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>\-Schnittstellenimplementierung, die aktuelle IntelliSens\-Funktionalität beizubehalten.  In den meisten Fällen bieten die Methoden der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>\-Schnittstelle eine Teilmenge von dar, was auf der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>\-Schnittstelle implementiert wird.  Die Teilmenge enthält Behandlung von IntelliSense Benutzeroberfläche, Caretzeichen\- und die Bearbeitung von Auswahl und einfacher Text.  Außerdem ermöglicht die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>\-Schnittstelle separates IntelliSense „Betreff“ und „Kontext“ damit IntelliSense für Themen bereitgestellt werden kann, die nicht direkt im Textpuffer befinden, der für Kontext verwendet wird.  
  
#### IVsIntellisenseHost.GetHostFlags  
 Ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> Anbieter muss die Schnittstellen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A>\-Methode implementieren, um einen Client zu ermöglichen, um zu bestimmen, welche Art von IntelliSense\-Funktionen der Host unterstützt.  
  
 Die Host Flags, definiert in [IntelliSenseHostFlags](../extensibility/intellisensehostflags.md), werden unten zusammengefasst.  
  
|IntelliSense\-Host\-Flag|Beschreibung|  
|------------------------------|------------------|  
|IHF\_READONLYCONTEXT|Dieses Flag festzulegen, bedeutet, dass der Kontextpuffer schreibgeschützt ist und nur innerhalb des abhängigen Text bearbeiten.|  
|IHF\_NOSEPERATESUBJECT|Dieses Flag festzulegen, bedeutet, dass kein separates IntelliSense\-Betreff vorhanden ist.  Der Betreff ist im Kontextpuffer, wie im herkömmlichen System <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> IntelliSense.|  
|IHF\_SINGLELINESUBJECT|Dieses Flag festzulegen, bedeutet, dass der Antragsteller nicht Mehrkanalfähiges ist, z. B. in einer Bearbeitung der einzelnen Zeile im **Überwachen** Fenster.|  
|IHF\_FORCECOMMITTOCONTEXT|Wenn dieses Flag festgelegt ist und der Kontextpuffer aktualisiert werden muss, kann der Host das auf dem Schreibschutzflag Kontextpuffer ignoriert, und die Bearbeitungen, um fortzufahren.|  
|IHF\_OVERTYPE|Das Bearbeiten oder Antragsteller \(im Kontext\) erfolgen soll, überschreiben Sie im Modus.|  
  
#### IVsIntellisenseHost.BeforeCompletorCommit und IVsIntellisenseHost.AfterCompletorCommit  
 Diese Rückrufmethoden werden vom Fenster schließen, bevor und nachdem Text übernommen wird aufgerufen, um eine Vorverarbeitung und Nachverarbeitung zu aktivieren.  
  
#### IVsIntellisenseCompletor  
 Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor>\-Schnittstelle ist eine CO\-erstellbare Version des standardmäßigen abschluss das Fenster in der integrierten Entwicklungsumgebung \(IDE\) verwendet wird.  Jede Schnittstelle kann IntelliSense <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> schnell implementieren, indem sie diese completor Schnittstelle verwendet.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.TextManager.Interop>