---
title: "Vorbereitung zum Debuggen: Visual&#160;C++-Projekttypen | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "Debugbuilds, Projekteinstellungen"
  - "Debuggen [C++]"
  - "Projektvorlagen, Debuggen"
  - "Visual C++-Projekte, Debuggen"
ms.assetid: 912b4ba2-7719-43d5-b087-db33e3f9329a
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Vorbereitung zum Debuggen: Visual&#160;C++-Projekttypen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Abschnitt wird das Debuggen grundlegender Projekttypen erläutert, die mithilfe von [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]\-Projektvorlagen erstellt wurden.  
  
 Beachten Sie, dass Projekttypen, die DLLs als Ausgabe erstellen, aufgrund ihrer gemeinsamen Features unter [Debuggen von DLL\-Projekten](../debugger/debugging-dll-projects.md) besprochen werden.  
  
##  <a name="BKMK_In_this_topic"></a> In diesem Thema  
 [Empfohlene Eigenschafteneinstellungen](#BKMK_Recommended_Property_Settings)  
  
 [Win32-Projekte](#BKMK_Win32_Projects)  
  
-   [So debuggen Sie eine in C oder C++ geschriebene Win32-Anwendung](#BKMK_To_debug_a_C_or_C___Win32_application)  
  
-   [So richten Sie eine Debugkonfiguration manuell ein](#BKMK_To_manually_set_a_Debug_configuration)  
  
 [Windows Forms-Anwendungen (.NET)](#BKMK_Windows_Forms_Applications___NET_)  
  
##  <a name="BKMK_Recommended_Property_Settings"></a> Empfohlene Eigenschafteneinstellungen  
 Bestimmte Eigenschaften sollten für alle Szenarios des nicht verwalteten Debuggens gleich festgelegt werden.  Die folgenden Tabellen zeigen die empfohlenen Eigenschafteneinstellungen.  Die hier nicht aufgeführten Einstellungen können je nach verwaltetem Projekttyp unterschiedlich sein.  Weitere Informationen finden Sie unter [Projekteinstellungen für eine C\+\+\-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)  
  
### Konfigurationseigenschaften &#124; C\/C\+\+ &#124; Knoten "Optimierung"  
  
|Eigenschaftenname|Einstellung|  
|-----------------------|-----------------|  
|**Optimierung**|Legen Sie diese Einstellung auf **Deaktiviert \(\/0d\)** fest. Optimierter Code ist schwieriger zu debuggen, da die generierten Anweisungen nicht direkt mit dem Quellcode übereinstimmen.  Wenn das Programm einen Fehler aufweist, der nur im optimierten Code auftritt, können Sie diese Einstellung aktivieren. Beachten Sie jedoch, dass der im **Disassembly**\-Fenster angezeigte Code aus optimiertem Code generiert wurde, der u. U. nicht mit dem Inhalt der Quellcodefenster übereinstimmt.  Andere Funktionen, z. B. die Ausführung in Einzelschritten, verhalten sich möglicherweise nicht wie erwartet.|  
  
### Konfigurationseigenschaften &#124; Linker &#124; Knoten "Debuggen"  
  
|Eigenschaftenname|Einstellung|  
|-----------------------|-----------------|  
|**Debuginformationen generieren**|Sie sollten diese Option beim Erstellen von Debugsymbolen und Dateien, die für das Debuggen benötigt werden, immer auf **Ja \(\/DEBUG\)** festlegen.  Wenn die Anwendung in Produktion geht, können Sie die Option wieder deaktivieren.|  
  
 [In diesem Thema](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Win32_Projects"></a> Win32\-Projekte  
 Win32\-Anwendungen sind herkömmliche in C oder C\+\+ geschriebene Windows\-Programme.  Das Debuggen dieses Anwendungstyps in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ist einfach.  
  
 Win32\-Anwendungen enthalten MFC\-Anwendungen und ATL\-Projekte.  Sie verwenden Windows\-APIs und u. U. auch MFC oder ATL, nutzen jedoch nicht die Common Language Runtime \(CLR\).  Sie können aber verwalteten Code aufrufen, der die CLR verwendet.  
  
 Die unten stehende Prozedur beschreibt, wie ein Win32\-Projekt aus [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] heraus gedebuggt wird.  Sie können eine Win32\-Anwendung jedoch auch debuggen, indem sie sie außerhalb von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] starten und dann eine Verbindung zu ihr herstellen.  Weitere Informationen finden Sie unter [Anhängen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
###  <a name="BKMK_To_debug_a_C_or_C___Win32_application"></a> So debuggen Sie eine in C oder C\+\+ geschriebene Win32\-Anwendung  
  
1.  Öffnen Sie das Projekt in Visual Studio.  
  
2.  Klicken Sie im Menü **Debuggen** auf **Starten**.  
  
3.  Debuggen Sie mit den in [Debugger – Grundlagen](../debugger/debugger-basics.md) besprochenen Techniken.  
  
###  <a name="BKMK_To_manually_set_a_Debug_configuration"></a> So richten Sie eine Debugkonfiguration manuell ein  
  
1.  Klicken Sie im Menü **Ansicht** auf die Option **Eigenschaftenseiten**.  
  
2.  Klicken Sie auf den Knoten **Konfigurationseigenschaften**, um diesen zu öffnen, sofern er nicht bereits geöffnet ist.  
  
3.  Wählen Sie **Allgemein** aus, und legen Sie den Wert der Zeile **Ausgabe** auf **Debuggen** fest.  
  
4.  Öffnen Sie den Knoten **C\/C\+\+**, und wählen Sie **Allgemein** aus.  
  
     Geben Sie in der Zeile **Debuggen** den Typ der Debuginformationen an, die vom Compiler generiert werden sollen.  Als Werte können Sie u. a. **Programmdatenbank \(\/Zi\)** oder **Programmdatenbank zum Bearbeiten und Fortfahren \(\/ZI\)** auswählen.  
  
5.  Wählen Sie **Optimierung** aus, und wählen Sie in der Zeile **Optimierung** aus der Dropdownliste die Option **Deaktiviert \(\/0d\)** aus.  
  
     Optimierter Code ist schwieriger zu debuggen, da die generierten Anweisungen nicht direkt mit dem Quellcode übereinstimmen.  Wenn das Programm einen Fehler aufweist, der nur im optimierten Code auftritt, können Sie diese Einstellung aktivieren. Beachten Sie jedoch, dass der im Disassembly\-Fenster angezeigte Code aus optimiertem Code generiert wurde, der u. U. nicht mit dem Inhalt der Quellcodefenster übereinstimmt.  Features wie die schrittweise Ausführung zeigen die Haltepunkte und den Ausführungspunkt möglicherweise nicht korrekt an.  
  
6.  Öffnen Sie den Knoten **Linker**, und wählen Sie **Debuggen** aus.  Wählen Sie in der ersten **Generieren**\-Zeile aus der Dropdownliste die Option **Ja \(\/DEBUG\)** aus.  Wählen Sie beim Debuggen immer diese Einstellung.  
  
 Weitere Informationen finden Sie unter [Projekteinstellungen für eine C\+\+\-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md) .  
  
 [In diesem Thema](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Windows_Forms_Applications___NET_"></a> Windows Forms\-Anwendungen \(.NET\)  
 Die Vorlage der **Windows Forms\-Anwendung \(.NET\)** erstellt eine [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]\-Windows Forms\-Anwendung.  Weitere Informationen finden Sie unter [How to: Create a Windows Application Project](http://msdn.microsoft.com/de-de/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
 Das Debuggen dieses Anwendungstyps in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ist mit dem Debuggen in verwalteten Windows Forms\-Anwendungen vergleichbar.  
  
 Wenn Sie ein Windows Forms\-Projekt mit der Projektvorlage erstellen, werden die erforderlichen Einstellungen für die Debug\- und Releasekonfigurationen automatisch durch [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] festgelegt.  Gegebenenfalls können Sie diese Einstellungen im Dialogfeld **\<Projektname\>\-Eigenschaftenseiten** ändern.  Weitere Informationen finden Sie unter [Debug\- und Releasekonfigurationen](../debugger/how-to-set-debug-and-release-configurations.md).  
  
 Weitere Informationen finden Sie unter [Projekteinstellungen für eine C\+\+\-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
 Eine weitere Möglichkeit zum Debuggen einer Windows Forms\-Anwendung besteht darin, die Anwendung außerhalb von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zu starten und dann eine Verbindung zu ihr herzustellen.  Weitere Informationen finden Sie unter [Anfügen an ein aktives Programm oder an mehrere Programme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 [In diesem Thema](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
## Siehe auch  
 [Debugger – Grundlagen](../debugger/debugger-basics.md)   
 [Projekteinstellungen für eine C\+\+\-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Anfügen an ein aktives Programm oder an mehrere Programme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Debug\- und Releasekonfigurationen](../debugger/how-to-set-debug-and-release-configurations.md)   
 [How to: Create a Windows Application Project](http://msdn.microsoft.com/de-de/b2f93fed-c635-4705-8d0e-cf079a264efa)