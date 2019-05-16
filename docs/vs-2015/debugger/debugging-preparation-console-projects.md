---
title: 'Vorbereitung des Debugvorgangs: Konsolenprojekte | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], console applications
- debugging console applications
- console applications, debugging
ms.assetid: 9641f1d9-2d5a-48b1-8731-6525e8f67892
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5ac87f6c5ef5fcf9fc7ca5532fe7436dedb8ba97
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65691220"
---
# <a name="debugging-preparation-console-projects"></a>Vorbereitung des Debugvorgangs: Konsolenprojekte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit Ausnahme einiger zusätzlicher Punkte ist die Vorbereitung für das Debuggen eines Konsolenprojekts der Vorbereitung für das Debuggen eines Windows-Projekts sehr ähnlich. Weitere Informationen finden Sie unter [Windows Forms-Anwendungen](../debugger/debugging-preparation-windows-forms-applications.md), und [Vorbereitung zum Debuggen: Windows Forms-Anwendungen (.NET)](https://msdn.microsoft.com/a8bc54de-41a3-464d-9a12-db9bdcbc1ad5). Wegen der Ähnlichkeit aller Konsolenanwendungen deckt dieses Thema die folgenden Projekttypen ab:  
  
- C#-Konsolenanwendung  
  
- Visual Basic-Konsolenanwendung  
  
- C++-Konsolenanwendung (.NET)  
  
- C++-Konsolenanwendung (Win32)  
  
  Für die Konsolenanwendung müssen u. U. Befehlszeilenargumente angegeben werden. Weitere Informationen finden Sie unter [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md), [Projekteinstellungen für eine Visual Basic-Debugkonfiguration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md), oder [Projekteinstellungen für c# Debug Configurations ](../debugger/project-settings-for-csharp-debug-configurations.md).  
  
  Wie alle Projekteigenschaften bleiben diese Argumente über die Debug- und Visual Studio-Sitzungen hinweg erhalten. Wenn die Konsolenanwendung zuvor bereits debuggt wurde, sollten Sie daran denken, dass im Dialogfeld **\<Projekt> Eigenschaftenseiten** noch Argumente aus früheren Sitzungen enthalten sein können.  
  
  Für die Eingabe und die Anzeige von Ausgabemeldungen verwendet eine Konsolenanwendung das Fenster **Konsole**. Zum Schreiben in die **Konsole** Fenster, die Ihre Anwendung verwenden muss die **Konsole** Objekt anstelle des Debug-Objekts. Verwenden Sie wie gewohnt das Debug-Objekt, um in das Fenster **Visual Studio-Ausgabe** zu schreiben. Sie sollten genau wissen, in welchem Fenster die Ausgabe erfolgt, da Sie ansonsten u. U. die Ausgabe im falschen Fenster überprüfen. Weitere Informationen finden Sie unter [Console-Klasse](https://msdn.microsoft.com/library/system.console.aspx), [Debug-Klasse](https://msdn.microsoft.com/library/system.diagnostics.debug.aspx) und [Ausgabefenster](../ide/reference/output-window.md).  
  
## <a name="starting-the-application"></a>Starten der Anwendung  
 Wenn einige Konsolenanwendungen gestartet werden, werden sie vollständig ausgeführt und dann beendet. Dieses Verhalten gibt Ihnen möglicherweise nicht genügend Zeit, um die Ausführung zu unterbrechen und einen Debugvorgang durchzuführen. Zum Debuggen einer Anwendung verwenden Sie eines der folgenden Verfahren, mit dem die Anwendung gestartet wird:  
  
- Die Anwendung beginnt mit der Ausführung und wird so lange ausgeführt, bis der Haltepunkt erreicht wird.  
  
- Die Anwendung wird gestartet und sofort an der ersten Zeile des Quellcodes unterbrochen.  
  
- In einem Quellcodefenster, klicken Sie auf eine Zeile aus, und wählen Sie **Ausführen bis Cursor**.  
  
   Die Anwendung wird gestartet und bis zur ausgewählten Zeile bzw. bis zu einem Haltepunkt ausgeführt, wenn der Haltepunkt vor der Zeile erreicht wird.  
  
  Beim Debuggen einer Konsolenanwendung möchten Sie die Anwendung möglicherweise über die Eingabeaufforderung und nicht von Visual Studio aus starten. In diesem Fall können Sie die Anwendung über die Eingabeaufforderung starten und den Visual Studio-Debugger an die Anwendung anfügen. Weitere Informationen finden Sie unter [Anfügen an ausgeführte Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
  Wenn Sie eine Konsolenanwendung in Visual Studio starten, wird das Fenster **Konsole** manchmal hinter dem Visual Studio-Fenster angezeigt. Wenn Sie die Konsolenanwendung über Visual Studio starten und anscheinend nichts geschieht, versuchen Sie, das Visual Studio-Fenster zu verschieben.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)   
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)   
 [Visual C++ Project Types (Visual C++-Projekttypen)](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [C#-, F#- und Visual Basic-Projekttypen](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Project Settings for a C++ Debug Configuration (Projekteinstellungen für eine C++-Debugkonfiguration)](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Debuggersicherheit](../debugger/debugger-security.md)
