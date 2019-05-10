---
title: IntelliSense-Hosting | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - IntelliSense hosting
ms.assetid: 20c61f8a-d32d-47e2-9c67-bf721e2cbead
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6e4f6ae0f2df20cefefb8a086fbd383d98a6d5cd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62910620"
---
# <a name="intellisense-hosting"></a>Hosten von IntelliSense
Visual Studio ermöglicht das Hosten von IntelliSense. IntellSense hosten können, bieten Sie IntelliSense für Code, der nicht von der Text-Editor für Visual Studio gehostet wird.

## <a name="intellisense-hosting-usage"></a>IntelliSense-Host-Nutzung
 In Visual Studio Code, der Zugriff auf einen Vervollständigungssatz und einen Textpuffer hat erhalten IntelliSense Windows von jedem beliebigen Standort in der Benutzeroberfläche (UI). Beispielszenarien für die dies sind die Vervollständigung in der **Watch** Fenster oder in das Feld "Bedingung" einen Haltepunkt Eigenschaftenfenster.

### <a name="implementation-interfaces"></a>Implementierung von Schnittstellen

#### <a name="ivsintellisensehost"></a>IVsIntellisenseHost
 Alle UI-Komponente, die IntelliSense-Popupfenster hostet muss unterstützen die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> Schnittstelle. Die Kern-Editor Text Standardansicht enthält eine Aktie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> schnittstellenimplementierung, um die aktuellen IntelliSense-Funktionalität beizubehalten. Zum größten Teil, die Methoden der der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> Schnittstelle dar, die eine Teilmenge von Was wird implementiert, auf die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Schnittstelle. Die Teilmenge enthält IntelliSense UI Behandlung, Einfügemarke und Markierung Manipulation und Ersatzfunktionen für einfachen Text an. Darüber hinaus die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> Schnittstelle ermöglicht, separate IntelliSense "Betreff" und "Kontext", sodass IntelliSense für Themen bereitgestellt werden kann, die nicht direkt im Textpuffer vorhanden sind, die für den Kontext verwendet wird.

#### <a name="ivsintellisensehostgethostflags"></a>IVsIntellisenseHost.GetHostFlags
 Ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> muss vom Anbieter der Schnittstelle implementiert die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A> Methode zum Aktivieren von eines Clients, um zu bestimmen, welche Art von IntelliSense auf den Host features unterstützt.

 Der hostflags, die in definierten [IntelliSenseHostFlags](../extensibility/intellisensehostflags.md), sind unten zusammengefasst.

|IntelliSense Host Flag|Beschreibung|
|----------------------------|-----------------|
|IHF_READONLYCONTEXT|Dieses Flag bedeutet, dass der Kontextpuffer festlegen tritt auf, nur-Lese und Bearbeitungsfunktionen nur innerhalb des Betreff-Texts.|
|IHF_NOSEPERATESUBJECT|Festlegen dieser Kennzeichnung bedeutet, die es ist keine separate IntelliSense-Thema. Der Antragsteller vorhanden im Kontextpuffer, z. B. der herkömmlichen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> IntelliSense-System.|
|IHF_SINGLELINESUBJECT|Dieses Flag bedeutet, dass der Antragsteller nicht festlegen kann, z. B. in einem einzeiligen Bearbeitung im mehrzeiligen der **sehen Sie sich** Fenster.|
|IHF_FORCECOMMITTOCONTEXT|Wenn dieses Flag wird festgelegt, und der Kontextpuffer aktualisiert werden muss, ermöglicht es dem Host, den Schreibschutz-Flag auf den Kontextpuffer, ignoriert werden sollen und Bearbeitungen, um den Vorgang fortzusetzen.|
|IHF_OVERTYPE|Bearbeiten (in den Betreff- oder kontextfeldern) sollte im Überschreibmodus durchgeführt werden.|

#### <a name="ivsintellisensehostbeforecompletorcommit-and-ivsintellisensehostaftercompletorcommit"></a>IVsIntellisenseHost.BeforeCompletorCommit und IVsIntellisenseHost.AfterCompletorCommit
 Die Rückrufmethoden heißen vom Abschluss Fenster vor und nach dem Text, aktivieren Sie die vorverarbeitung und Nachbearbeitung gespeichert wird.

#### <a name="ivsintellisensecompletor"></a>IVsIntellisenseCompletor
 Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor> Schnittstelle ist ein gemeinsam erstellbares Version des standardmäßigen Beendigungsmodus Fensters, das von der integrierten Entwicklungsumgebung (IDE) verwendet wird. Alle <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> Benutzeroberfläche kann schnell IntelliSense mithilfe dieser Completor-Schnittstelle implementieren.

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.TextManager.Interop>