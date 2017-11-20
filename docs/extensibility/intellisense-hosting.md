---
title: Hosten von IntelliSense | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - IntelliSense hosting
ms.assetid: 20c61f8a-d32d-47e2-9c67-bf721e2cbead
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 850e4b2ef6d455bb141827fa125c4c7c6860b652
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="intellisense-hosting"></a>Hosten von IntelliSense
Visual Studio ermöglicht das Hosten von IntelliSense. IntellSense hosten können, geben Sie IntelliSense für Code, der nicht von der Text-Editor von Visual Studio gehostet wird.  
  
## <a name="intellisense-hosting-usage"></a>IntelliSense-Hosting-Verwendung  
 In Visual Studio jeglicher Code, der Zugriff auf einen Abschluss Satz und einen Textpuffer hat erhalten IntelliSense Windows von jedem beliebigen Standort in der Benutzeroberfläche (UI). Einige Beispielszenarien dieses sind Abschluss in der **Überwachen** Fenster oder im Feld "Bedingung" eines Haltepunkt-Eigenschaften-Fensters.  
  
### <a name="implementation-interfaces"></a>Implementierung von Schnittstellen  
  
#### <a name="ivsintellisensehost"></a>IVsIntellisenseHost  
 Jede Benutzeroberflächenkomponente, die IntelliSense-Popupfenster hostet muss unterstützen die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> Schnittstelle. Die Standardansicht Core Editor Text enthält ein Aktienkurs <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> -schnittstellenimplementierung, um die aktuellen IntelliSense-Funktionalität beizubehalten. Meistens, die Methoden der der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> Schnittstelle dar, die eine Teilmenge der Elemente wird implementiert, auf die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Schnittstelle. Die Teilmenge enthält IntelliSense UI Behandlung, Caretzeichen und Auswahl Manipulation und einfachen Text-Ersatzfunktionalität. Darüber hinaus die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> Schnittstelle ermöglicht separate IntelliSense "Subject" und "Kontext" so, dass IntelliSense für Themen bereitgestellt werden kann, die nicht direkt in den Textpuffer vorhanden sind, die für den Kontext verwendet wird.  
  
#### <a name="ivsintellisensehostgethostflags"></a>IVsIntellisenseHost.GetHostFlags  
 Ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> muss vom Anbieter Schnittstelle implementiert die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A> Methode zum Aktivieren von eines Clients, um zu bestimmen, welche Art von IntelliSense-Funktionen den Host unterstützt.  
  
 Host-Flags, die in definierten [IntelliSenseHostFlags](../extensibility/intellisensehostflags.md), sind unten zusammengefasst.  
  
|IntelliSense-Host-Flag|Beschreibung|  
|----------------------------|-----------------|  
|IHF_READONLYCONTEXT|Dieses Flag darauf hin, dass die Kontextpuffer festlegen tritt auf, nur-Lese und Bearbeitung nur innerhalb der Betreffzeile.|  
|IHF_NOSEPERATESUBJECT|Festlegen dieser Kennzeichnung bedeutet, die es ist keine separate IntelliSense-Antragsteller. Das Subjekt vorhanden in den Kontextpuffer wie in der herkömmlichen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> IntelliSense-System.|  
|IHF_SINGLELINESUBJECT|Dieses Flag darauf hin, dass das Subjekt nicht festlegen mehrzeilige fähig, z. B. in einer einzelnen Zeile bearbeiten, der **Überwachen** Fenster.|  
|IHF_FORCECOMMITTOCONTEXT|Wenn dieses Flag festgelegt ist, und der Kontextpuffer aktualisiert werden muss, ermöglicht es dem Host, der nur-Lese Flag auf den Kontextpuffer ignoriert werden soll, und bearbeiten, um den Vorgang fortzusetzen.|  
|IHF_OVERTYPE|Bearbeitung (im Antragstellernamen oder Kontextmenü) sollte im Überschreibmodus erfolgen.|  
  
#### <a name="ivsintellisensehostbeforecompletorcommit-and-ivsintellisensehostaftercompletorcommit"></a>IVsIntellisenseHost.BeforeCompletorCommit und IVsIntellisenseHost.AfterCompletorCommit  
 Dieser Rückrufmethoden werden von der Fenster zur tagvervollständigung aufgerufen, vor und nach dem Text, an die vorverarbeitung und nach der Verarbeitung zu ermöglichen, übergeben wird.  
  
#### <a name="ivsintellisensecompletor"></a>IVsIntellisenseCompletor  
 Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor> Schnittstelle ist ein gemeinsam erstellbares Version von standard-Abschluss-Fenster, das von der integrierten Entwicklungsumgebung (IDE) verwendet wird. Alle <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> Benutzeroberfläche kann schnell IntelliSense unter Verwendung dieser Schnittstelle Completor implementieren.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.TextManager.Interop>