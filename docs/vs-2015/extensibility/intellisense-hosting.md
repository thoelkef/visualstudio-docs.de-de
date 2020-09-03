---
title: IntelliSense-Hosting | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - IntelliSense hosting
ms.assetid: 20c61f8a-d32d-47e2-9c67-bf721e2cbead
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a5c378aec6822a436de0d8fc2656fcac7be4149f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203894"
---
# <a name="intellisense-hosting"></a>IntelliSense-Hosting
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio ermöglicht das IntelliSense-Hosting. Mit dem intellsense-Hosting können Sie IntelliSense für Code bereitstellen, der nicht vom Text-Editor von Visual Studio gehostet wird.  
  
## <a name="intellisense-hosting-usage"></a>IntelliSense-hostingverwendung  
 In Visual Studio kann jeder Code, der auf einen Vervollständigungs Satz und einen Text Puffer zugreifen kann, IntelliSense-Fenster von jedem beliebigen Ort in der Benutzeroberfläche (UI) abrufen. Einige Beispielszenarien hierfür sind der Abschluss im Fenster über **Wachen** oder im Feld Bedingung eines Eigenschaften Fensters für Haltepunkte.  
  
### <a name="implementation-interfaces"></a>Implementierungs Schnittstellen  
  
#### <a name="ivsintellisensehost"></a>Ivsintellisenonhost  
 Jede Benutzeroberflächen Komponente, die IntelliSense-Popup Fenster hostet, muss die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> Schnittstelle unterstützen. Die Textansicht des Standard-Core-Editors enthält eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> Implementierung der-Schnittstelle, um die aktuelle IntelliSense-Funktionalität beizubehalten. In den meisten Fällen stellen die Methoden der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> Schnittstelle eine Teilmenge der Elemente dar, die auf der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Schnittstelle implementiert werden. Die Teilmenge umfasst die IntelliSense-UI-Behandlung, Einfügemarke und Auswahl Bearbeitung sowie einfache Text Ersetzungs Funktionen. Außerdem ermöglicht die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> Schnittstelle separate IntelliSense-"Betreff" und "Kontext", damit IntelliSense für Themen bereitgestellt werden kann, die nicht direkt im Text Puffer vorhanden sind, der für den Kontext verwendet wird.  
  
#### <a name="ivsintellisensehostgethostflags"></a>Ivsintellisenonhost. GetHostFlags  
 Ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> Schnittstellen Anbieter muss die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A> Methode implementieren, damit ein Client ermitteln kann, welche Art von IntelliSense-Funktionen der Host unterstützt.  
  
 Die in [intellisenabhostflags](../extensibility/intellisensehostflags.md)definierten hostflags werden unten zusammengefasst.  
  
|IntelliSense-hostflag|BESCHREIBUNG|  
|----------------------------|-----------------|  
|IHF_READONLYCONTEXT|Wenn dieses Flag festgelegt wird, ist der Kontext Puffer schreibgeschützt, und die Bearbeitung erfolgt nur innerhalb des betrefftexts.|  
|IHF_NOSEPERATESUBJECT|Das Festlegen dieses Flags bedeutet, dass kein separater IntelliSense-Betreff vorhanden ist. Der Betreff ist im Kontext Puffer vorhanden, z. b. im herkömmlichen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> IntelliSense-System.|  
|IHF_SINGLELINESUBJECT|Das Festlegen dieses Flags bedeutet, dass der Betreff nicht mehrzeilige fähig ist, z. b. in einer einzelnen Zeilen Bearbeitung im **Überwachungs** Fenster.|  
|IHF_FORCECOMMITTOCONTEXT|Wenn dieses Flag festgelegt ist und der Kontext Puffer aktualisiert werden muss, aktiviert der Host das schreibgeschützte Flag des Kontext Puffers, um den Vorgang fortzusetzen.|  
|IHF_OVERTYPE|Die Bearbeitung (im Betreff oder Kontext) sollte im über Schreib-Modus erfolgen.|  
  
#### <a name="ivsintellisensehostbeforecompletorcommit-and-ivsintellisensehostaftercompletorcommit"></a>Ivsintellisenonhost. beforecompletor Commit und ivsintellisenabst. aftercompletor Commit  
 Diese Rückruf Methoden werden vom Vervollständigungs Fenster vor und nach dem Commit von Text aufgerufen, um die Vorverarbeitung und Nachbearbeitung zu ermöglichen.  
  
#### <a name="ivsintellisensecompletor"></a>Ivsintellisenabversitor  
 Die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor> Schnittstelle ist eine zusammen gearbeitbare Version des Standard Vervollständigungs Fensters, das von der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) verwendet wird. Eine beliebige <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> Schnittstelle kann IntelliSense schnell mithilfe dieser Completor-Schnittstelle implementieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.VisualStudio.TextManager.Interop>
