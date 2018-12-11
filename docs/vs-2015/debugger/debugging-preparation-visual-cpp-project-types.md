---
title: 'Vorbereitung zum Debuggen: Visual C++-Projekt Typen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- project templates, debugging
- Visual C++ projects, debugging
- debug builds, project settings
- debugging [C++]
ms.assetid: 912b4ba2-7719-43d5-b087-db33e3f9329a
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 802b34d47501d3538008838f9bb6ddec93ac827a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752399"
---
# <a name="debugging-preparation-visual-c-project-types"></a>Vorbereitung zum Debuggen: Visual C++-Projekttypen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Abschnitt wird das Debuggen grundlegender Projekttypen erläutert, die mithilfe von [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]-Projektvorlagen erstellt wurden.  
  
 Beachten Sie, die Projekttypen, die zum Erstellen von DLLs als Ausgabe in gruppiert wurden [Debuggen von DLL-Projekten](../debugger/debugging-dll-projects.md) aufgrund der gemeinsamen Features.  
  
##  <a name="BKMK_In_this_topic"></a> In diesem Thema  
 [Empfohlene eigenschafteneinstellungen](#BKMK_Recommended_Property_Settings)  
  
 [Win32-Projekte](#BKMK_Win32_Projects)  
  
- [Debuggen eine C- oder C++ geschriebene Win32-Anwendung](#BKMK_To_debug_a_C_or_C___Win32_application)  
  
- [Eine Debugkonfiguration manuell festlegen](#BKMK_To_manually_set_a_Debug_configuration)  
  
  [Windows Forms-Anwendungen (.NET)](#BKMK_Windows_Forms_Applications___NET_)  
  
##  <a name="BKMK_Recommended_Property_Settings"></a> Empfohlene eigenschafteneinstellungen  
 Bestimmte Eigenschaften sollten für alle Szenarios des nicht verwalteten Debuggens gleich festgelegt werden. Die folgenden Tabellen zeigen die empfohlenen Eigenschafteneinstellungen. Die hier nicht aufgeführten Einstellungen können je nach verwaltetem Projekttyp unterschiedlich sein. Weitere Informationen finden Sie unter [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)  
  
### <a name="configuration-properties-124-cc-124-optimization-node"></a>Konfigurationseigenschaften &#124; C/C++- &#124; Knoten "Optimierung"  
  
|Eigenschaftenname|Einstellung|  
|-------------------|-------------|  
|**Optimization**|Legen Sie auf **deaktiviert (/ 0d).** Optimierter Code ist schwieriger zu debuggen, da die generierten Anweisungen nicht direkt mit dem Quellcode übereinstimmen. Wenn Sie feststellen, das Programm hat einen Fehler, der nur im optimierten Code auftritt, können Sie diese Einstellung aktivieren, aber denken Sie daran, im gezeigten Code der **Disassembly** aus optimiertem, die nicht mit sehen Sie in Ihrer Quelle generiert wurde Windows. Andere Funktionen, z. B. die Ausführung in Einzelschritten, verhalten sich möglicherweise nicht wie erwartet.|  
  
### <a name="configuration-properties-124-linker-124-debugging-node"></a>Konfigurationseigenschaften &#124; Linker &#124; Knoten "Debuggen"  
  
|Eigenschaftenname|Einstellung|  
|-------------------|-------------|  
|**Debuginformationen generieren**|Legen Sie diese Option immer auf **Ja (/ DEBUG)** zum Erstellen von Debugsymbolen und Dateien, die für das Debuggen erforderlich. Wenn die Anwendung in Produktion geht, können Sie die Option wieder deaktivieren.|  
  
 [Inhalt](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Win32_Projects"></a> Win32-Projekte  
 Win32-Anwendungen sind herkömmliche in C oder C++ geschriebene Windows-Programme. Das Debuggen dieses Anwendungstyps in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ist einfach.  
  
 Win32-Anwendungen enthalten MFC-Anwendungen und ATL-Projekte. Sie verwenden Windows-APIs und u. U. auch MFC oder ATL, nutzen jedoch nicht die Common Language Runtime (CLR). Sie können aber verwalteten Code aufrufen, der die CLR verwendet.  
  
 Die unten stehende Prozedur beschreibt, wie ein Win32-Projekt aus [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] heraus gedebuggt wird. Sie können eine Win32-Anwendung jedoch auch debuggen, indem sie sie außerhalb von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] starten und dann eine Verbindung zu ihr herstellen. Weitere Informationen finden Sie unter [Anfügen an ausgeführte Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
###  <a name="BKMK_To_debug_a_C_or_C___Win32_application"></a> Debuggen eine C- oder C++ geschriebene Win32-Anwendung  
  
1.  Öffnen Sie das Projekt in Visual Studio.  
  
2.  Auf der **Debuggen** Menü wählen **starten**.  
  
3.  Debuggen Sie mit die vorgestellten [Debugger – Grundlagen](../debugger/debugger-basics.md).  
  
###  <a name="BKMK_To_manually_set_a_Debug_configuration"></a> Eine Debugkonfiguration manuell festlegen  
  
1. Auf der **Ansicht** Menü klicken Sie auf **Eigenschaftenseiten**.  
  
2. Klicken Sie auf die **Konfigurationseigenschaften** Knoten aus, um es zu öffnen, ist dies nicht bereits  
  
3. Wählen Sie **allgemeine**, und legen Sie den Wert, der die **Ausgabe** Datenzeile zu aktivieren, **Debuggen**.  
  
4. Öffnen der **C/C++-** Knoten, und wählen **allgemeine**.  
  
    In der **Debuggen** Zeile, die Sie angeben, dass den Typ der Debuginformationen vom Compiler generiert werden soll. Werte ausgewählt werden kann, sind **Programmdatenbank (/ Zi)** oder **Programmdatenbank zum Bearbeiten und Fortfahren (/ Zi)**.  
  
5. Wählen Sie **Optimierung**, und klicken Sie in der **Optimierung** Zeile **deaktiviert (/ 0d)** aus der Dropdown-Liste.  
  
    Optimierter Code ist schwieriger zu debuggen, da die generierten Anweisungen nicht direkt mit dem Quellcode übereinstimmen. Wenn das Programm einen Fehler aufweist, der nur im optimierten Code auftritt, können Sie diese Einstellung aktivieren. Beachten Sie jedoch, dass der im Disassembly-Fenster angezeigte Code aus optimiertem Code generiert wurde, der u. U. nicht mit dem Inhalt der Quellcodefenster übereinstimmt. Funktionen wie die schrittweise Ausführung zeigen die Haltepunkte und den Ausführungspunkt möglicherweise nicht korrekt an.  
  
6. Öffnen der **Linker** Knoten, und wählen **Debuggen**. In der ersten **generieren** Zeile **Ja (/ DEBUG)** aus der Dropdown-Liste. Wählen Sie beim Debuggen immer diese Einstellung.  
  
   Weitere Informationen finden Sie unter[Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
   [Inhalt](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Windows_Forms_Applications___NET_"></a> Windows Forms-Anwendungen (.NET)  
 Die **Windows Forms-Anwendung (.NET)** Vorlage erstellt eine [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] Windows Forms-Anwendung. Weitere Informationen finden Sie unter [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
 Das Debuggen dieses Anwendungstyps in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ist mit dem Debuggen in verwalteten Windows Forms-Anwendungen vergleichbar.  
  
 Wenn Sie ein Windows Forms-Projekt mit der Projektvorlage erstellen, werden die erforderlichen Einstellungen für die Debug- und Releasekonfigurationen automatisch durch [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] festgelegt. Wenn erforderlich, Sie können diese Einstellungen im Ändern der  **\<Projektname > Eigenschaftenseiten** Dialogfeld. Weitere Informationen finden Sie unter [Debug- und Releasekonfigurationen](../debugger/how-to-set-debug-and-release-configurations.md).  
  
 Weitere Informationen finden Sie unter [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
 Eine weitere Möglichkeit zum Debuggen einer Windows Forms-Anwendung besteht darin, die Anwendung außerhalb von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zu starten und anschließend eine Verbindung zu ihr herzustellen. Weitere Informationen finden Sie unter [Anfügen an ein aktives Programm oder an mehrere Programme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 [Inhalt](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
## <a name="see-also"></a>Siehe auch  
 [Debugger – Grundlagen](../debugger/debugger-basics.md)   
 [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Anfügen an ein aktives Programm oder an mehrere Programme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Debug- und Releasekonfigurationen](../debugger/how-to-set-debug-and-release-configurations.md)   
 [Vorgehensweise: Erstellen eines Windows-Anwendungsprojekts](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)



