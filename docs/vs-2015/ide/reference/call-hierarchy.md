---
title: Aufrufhierarchie | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.CallHierarchy
helpviewer_keywords:
- Call Hierarchy
ms.assetid: c55bda01-d7de-4823-8f9a-1bcc37dbb74a
caps.latest.revision: 45
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 41c7aa12e4adf2a757689670cdfed394f2a534c6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433702"
---
# <a name="call-hierarchy"></a>Aufrufhierarchie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Mithilfe der Aufrufhierarchie können Sie in Ihrem Code navigieren, indem Sie alle Aufrufe von und aus einer ausgewählten Methode, Eigenschaft oder einem Konstruktor anzeigen. Dadurch können Sie besser verstehen, wie Code fließt und die Auswirkungen von Codeänderungen auswerten. Sie können mehrere Codeebenen überprüfen, um komplexe Verkettungen von Methodenaufrufen und zusätzlichen Einstiegspunkten in den Code zu sehen. Dadurch können Sie nach sämtlichen möglichen Ausführungspfaden suchen.  
  
 Die Aufrufhierarchie ist im Gegensatz zur Aufrufliste, die vom Debugger angezeigt wird, zur Entwurfszeit verfügbar.  
  
## <a name="using-call-hierarchy"></a>Verwenden der Aufrufhierarchie  
 Klicken Sie mit der rechten Maustaste auf Methode, Eigenschaft oder Konstruktoraufruf, damit das Fenster **Aufrufhierarchie** angezeigt wird, und klicken Sie anschließend auf **Aufrufhierarchie anzeigen**.  
  
 Der Membername erscheint in einem Strukturansichtsbereich im Fenster **Aufrufhierarchie**. Wenn Sie den Memberknoten erweitern, werden die Unterknoten **Calls To** _Membername_ (eingehende Aufrufe) und **Calls From** _Membername_ (ausgehende Aufrufe) angezeigt. In der folgenden Abbildung werden diese Knoten im Fenster **Aufrufhierarchie** angezeigt.  
  
 ![Aufrufhierarchie mit einem geöffneten Knoten](../../ide/reference/media/onenode.png "OneNode")  
Fenster „Aufrufhierarchie“  
  
- Wenn Sie den **Calls To**-Knoten erweitern, werden alle Members angezeigt, die den ausgewählten Member aufrufen.  
  
- Wenn Sie den **Calls From**-Knoten erweitern, werden alle Members angezeigt, die den ausgewählten Member aufrufen.  
  
  Anschließend können Sie sämtliche dieser Unterknotenmembers auf **Calls To**- und **Calls From**-Knoten erweitern. Dadurch können Sie, wie in der folgenden Abbildung dargestellt, in den Aufruferstapel navigieren.  
  
  ![Aufrufhierarchie: Mehrere Knoten geöffnet](../../ide/media/multiplenodes.png "MultipleNodes")  
  Fenster „Aufrufhierarchie“  
  
  Für Members, die als virtuell oder abstrakt definiert sind, wird ein **Overrides method name**-Knoten (Knoten zur Außerkraftsetzung des Methodennamens) angezeigt. Für Schnittstellenmember wird ein Knoten zum **Implementieren des Methodennamens** angezeigt. Diese erweiterbaren Knoten erscheinen auf derselben Ebene wie **Calls To**- und **Calls From**-Knoten.  
  
  Das Feld **Suchbereich** in der Symbolleiste enthält verschiedene Auswahlmöglichkeiten für **My Solution** („Meine Projektmappe“), **Aktuelles Projekt** und **Aktuelles Dokument**.  
  
  Wenn Sie im Strukturansichtsbereich **Aufrufhierarchie** einen untergeordneten Member auswählen:  
  
- Im Detailbereich **Aufrufhierarchie** werden alle Codezeilen angezeigt, in denen dieser untergeordnete Member von dem übergeordneten Member aufgerufen wird.  
  
- Wenn das **Codedefinitionsfenster** geöffnet ist, zeigt es den Code für den ausgewählten Member an. Dieses Fenster ist in C# und C++ verfügbar. Weitere Informationen zu diesem Fenster finden Sie unter [Anzeigen der Codestruktur](../../ide/viewing-the-structure-of-code.md).  
  
> [!NOTE]
> Die Aufrufhierarchie findet keine Methodengruppenverweise, die Stellen enthalten, an denen eine Methode als Ereignishandler hinzugefügt oder einem Delegaten zugewiesen wird. Verwenden Sie den Befehl **Alle Verweise suchen**, um alle Verweise auf eine Methode zu suchen.  
  
## <a name="shortcut-menu-items"></a>Kontextmenüelemente  
 In der folgenden Tabelle werden einige Kontextmenüoptionen beschrieben, auf die Sie zugreifen können, wenn Sie mit der rechten Maustaste auf einen Knoten im Strukturansichtsbereich klicken.  
  
|Kontextmenüelement|Beschreibung|  
|-----------------------|-----------------|  
|**Als neuen Stamm hinzufügen**|Fügt dem Strukturansichtsbereich den ausgewählten Knoten als neuen Stammknoten hinzu. Dadurch können Sie sich auf eine bestimmte Unterstruktur konzentrieren.|  
|**Stamm entfernen**|Entfernt den ausgewählten Stammknoten aus dem Strukturansichtsbereich. Diese Option ist nur in einem Stammknoten verfügbar.<br /><br /> Sie können außerdem die Symbolleistenschaltfläche **Stamm entfernen** verwenden, um den ausgewählten Stammknoten zu entfernen.|  
|**Gehe zu Definition**|Führt den Befehl „Gehe zu Definition“ für den ausgewählten Knoten aus. Dadurch wird zu der ursprünglichen Definition für einen Memberaufruf oder eine Variablendefinition navigiert.<br /><br /> Sie können auch auf den ausgewählten Knoten doppelklicken, oder drücken Sie für den ausgewählten Knoten auf F12, um den Befehl „Gehe zu Definition“ auszuführen.|  
|**Alle Verweise suchen**|Führt den Befehl „Alle Verweise suchen“ für den ausgewählten Knoten aus. So finden Sie alle Codezeilen in Ihrem Projekt, die auf eine Klasse oder einen Member verweisen.<br /><br /> Sie können auch auf UMSCHALT+F12 drücken, um den Befehl „Alle Verweise suchen“ für den ausgewählten Knoten auszuführen.|  
|**Kopieren**|Kopiert die Inhalte des ausgewählten Knotens (aber nicht dessen Unterknoten).|  
|**Aktualisieren**|Reduziert die ausgewählten Knoten, sodass bei der erneuten Erweiterung aktuelle Informationen angezeigt werden.|
