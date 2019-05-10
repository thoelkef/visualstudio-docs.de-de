---
title: Visual C#-Codeausschnitte | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- snippets [C#], default snippets
- snippets [C#], Code Snippet Inserter
- Code Snippet Inserter [J#]
- Code Snippet Inserter [C#]
- Visual C#, default snippets
ms.assetid: dbea3dd6-e650-4190-b874-c9f097d7de6e
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 47658a8aec8b2dedd2dcdeb337bdca805e1b0bca
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54787104"
---
# <a name="visual-c-code-snippets"></a>Visual C#-Codeausschnitte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Codeausschnitte sind vorgefertigte Ausschnitte aus Code, die Sie schnell in Ihren Code einfügen können. Beispielsweise erstellt der `for`-Codeausschnitt eine leere `for`-Schleife. Einige Codeausschnitte sind umschließende Codeausschnitte, mit deren Hilfe Sie Codezeilen markieren und dann einen Codeausschnitt auswählen können, der die markierten Codezeilen einschließt. Durch das Markieren von Codezeilen und das anschließende Aktivieren des `for`-Codeausschnitts wird beispielsweise eine `for`-Schleife erstellt, die die markierten Codezeilen innerhalb des Schleifenblocks enthält. Durch Codeausschnitte kann das Erstellen von Programmcode schneller, einfacher und zuverlässiger werden.  
  
 Sie können einen Codeausschnitt an der Cursorposition einfügen oder einen umgebenden Codeausschnitt einfügen, der den aktuell ausgewählten Code einschließt. Der Codeausschnitteinfüger wird im Menü **IntelliSense** über die Befehle **Codeausschnitt einfügen** oder **Umschließen mit** oder durch die Tastenkombinationen STRG+K und dann X, bzw. STRG+K gefolgt von S aufgerufen.  
  
 Der Codeausschnitteinfüger zeigt den Codeausschnittnamen für alle verfügbaren Codeausschnitte an. Darüber hinaus umfasst der Codeausschnitteinfüger ein Eingabedialogfeld, in dem Sie den Namen des Codeausschnitts vollständig oder teilweise eingeben können. Daraufhin wird im Codeausschnitteinfüger der Eintrag hervorgehoben, der dem Namen eines Codeausschnitts am besten entspricht. Durch Drücken der TAB-TASTE können Sie den Codeausschnitteinfüger jederzeit schließen und den derzeit ausgewählten Codeausschnitt einfügen. Durch Drücken von ESC oder Klicken mit der Maus im Code-Editor wird der Codeausschnitteinfüger geschlossen, ohne dass ein Codeausschnitt eingefügt wird.  
  
## <a name="default-code-snippets"></a>Standardcodeausschnitte  
 Die folgenden Codeausschnitte sind standardmäßig in Visual Studio enthalten.  
  
|Name (oder Verknüpfung)|Beschreibung|Mögliche Stellen zum Einfügen des Ausschnitts|  
|--------------------------|-----------------|---------------------------------------|  
|#if|Erstellt eine [#if](http://msdn.microsoft.com/library/48cabbff-ca82-491f-a56a-eeccd528c7c2)-Direktive und eine [#endif](http://msdn.microsoft.com/library/6a5fca55-5aee-441f-86f6-1c99fbe9ec05)-Direktive.|Beliebig.|  
|#region|Erstellt eine [#region](http://msdn.microsoft.com/library/672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4)-Direktive und eine [#endregion](http://msdn.microsoft.com/library/16099660-91b2-49e5-9646-77f9ef069526)-Direktive.|Beliebig.|  
|~|Erstellt einen Destruktor für die enthaltende Klasse.|Innerhalb einer Klasse.|  
|Attribut|Erstellt eine Deklaration für eine <xref:System.Attribute> abgeleitete Klasse.|In einem Namespace (einschließlich des globalen Namespaces), einer Klasse oder einer Struktur.|  
|checked|Erstellt einen [checked](http://msdn.microsoft.com/library/718a1194-988d-48a3-b089-d6ee8bd1608d)-Block.|In einer Methode, einem Indexer, einem Eigenschaftenaccessor oder einem Ereignisaccessor.|  
|Klasse|Erstellt eine Klassendeklaration.|In einem Namespace (einschließlich des globalen Namespaces), einer Klasse oder einer Struktur.|  
|ctor|Erstellt einen Konstruktor für die enthaltende Klasse.|Innerhalb einer Klasse.|  
|cw|Erstellt einen Aufruf an <xref:System.Console.WriteLine%2A>.|In einer Methode, einem Indexer, einem Eigenschaftenaccessor oder einem Ereignisaccessor.|  
|do|Erstellt eine [do](http://msdn.microsoft.com/library/50725f79-9ba6-4898-aa78-6e331568a1bb)`while`-Schleife.|In einer Methode, einem Indexer, einem Eigenschaftenaccessor oder einem Ereignisaccessor.|  
|else|Erstellt einen [else](http://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2)-Block.|In einer Methode, einem Indexer, einem Eigenschaftenaccessor oder einem Ereignisaccessor.|  
|enum|Erstellt eine [enum](http://msdn.microsoft.com/library/bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c)-Deklaration.|In einem Namespace (einschließlich des globalen Namespaces), einer Klasse oder einer Struktur.|  
|equals|Erstellt eine Methodendeklaration, die die in der <xref:System.Object>-Klasse definierte <xref:System.Object.Equals%2A>-Methode außer Kraft setzt.|Innerhalb einer Klasse oder Struktur.|  
|exception|Erstellt eine Deklaration für eine Klasse, die von einer Ausnahme abgeleitet wird (standardmäßig <xref:System.Exception>).|In einem Namespace (einschließlich des globalen Namespaces), einer Klasse oder einer Struktur.|  
|for|Erstellt eine [for](http://msdn.microsoft.com/library/34041a40-2c87-467a-9ffb-a0417d8f67a8)-Schleife.|In einer Methode, einem Indexer, einem Eigenschaftenaccessor oder einem Ereignisaccessor.|  
|foreach|Erstellt eine [foreach](http://msdn.microsoft.com/library/5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec)-Schleife.|In einer Methode, einem Indexer, einem Eigenschaftenaccessor oder einem Ereignisaccessor.|  
|forr|Erstellt eine [for](http://msdn.microsoft.com/library/34041a40-2c87-467a-9ffb-a0417d8f67a8)-Schleife, deren Schleifenvariable nach jeder Iteration verringert wird.|In einer Methode, einem Indexer, einem Eigenschaftenaccessor oder einem Ereignisaccessor.|  
|if|Erstellt einen [if](http://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2)-Block.|In einer Methode, einem Indexer, einem Eigenschaftenaccessor oder einem Ereignisaccessor.|  
|Indexer|Erstellt eine Indexerdeklaration.|Innerhalb einer Klasse oder Struktur.|  
|interface|Erstellt eine [interface](http://msdn.microsoft.com/library/7da38e81-4f99-4bc5-b07d-c986b687eeba)-Deklaration.|In einem Namespace (einschließlich des globalen Namespaces), einer Klasse oder einer Struktur.|  
|invoke|Erstellt einen Block, durch den ein Ereignis sicher aufgerufen wird.|In einer Methode, einem Indexer, einem Eigenschaftenaccessor oder einem Ereignisaccessor.|  
|Iterator|Erstellt einen Iterator.|Innerhalb einer Klasse oder Struktur.|  
|iterindex|Erstellt ein „benanntes“ Iterator-/Indexerpaar unter Verwendung einer geschachtelten Klasse.|Innerhalb einer Klasse oder Struktur.|  
|lock|Erstellt einen [lock](http://msdn.microsoft.com/library/656da1a4-707e-4ef6-9c6e-6d13b646af42)-Block.|In einer Methode, einem Indexer, einem Eigenschaftenaccessor oder einem Ereignisaccessor.|  
|mbox|Erstellt einen Aufruf an <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName>. Sie müssen möglicherweise einen Verweis auf „System.Windows.Forms.dll“ hinzufügen.|In einer Methode, einem Indexer, einem Eigenschaftenaccessor oder einem Ereignisaccessor.|  
|namespace|Erstellt eine [namespace](http://msdn.microsoft.com/library/0a788423-9110-42e0-97d9-bda41ca4870f)-Deklaration.|In einem Namespace (einschließlich des globalen Namespaces).|  
|prop|Erstellt eine Deklaration mit [automatisch implementierter Eigenschaft](http://msdn.microsoft.com/library/aa55fa97-ccec-431f-b5e9-5ac789fd32b7).|Innerhalb einer Klasse oder Struktur.|  
|propfull|Erstellt eine Eigenschaftendeklaration mit get-Accessor und set-Accessor.|Innerhalb einer Klasse oder Struktur.|  
|propg|Erstellt eine schreibgeschützte [automatisch implementierte Eigenschaft](http://msdn.microsoft.com/library/aa55fa97-ccec-431f-b5e9-5ac789fd32b7) mit einem privaten „set“-Accessor.|Innerhalb einer Klasse oder Struktur.|  
|sim|Erstellt eine Deklaration der Main-Methode mit [static](http://msdn.microsoft.com/library/5509e215-2183-4da3-bab4-6b7e607a4fdf)[int](http://msdn.microsoft.com/library/212447b4-5d2a-41aa-88ab-84fe710bdb52).|Innerhalb einer Klasse oder Struktur.|  
|struct|Erstellt eine [struct](http://msdn.microsoft.com/library/ff3dd9b7-dc93-4720-8855-ef5558f65c7c)-Deklaration.|In einem Namespace (einschließlich des globalen Namespaces), einer Klasse oder einer Struktur.|  
|svm|Erstellt eine Deklaration der Main-Methode mit [static](http://msdn.microsoft.com/library/5509e215-2183-4da3-bab4-6b7e607a4fdf)[void](http://msdn.microsoft.com/library/0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4).|Innerhalb einer Klasse oder Struktur.|  
|switch|Erstellt einen [switch](http://msdn.microsoft.com/library/44bae8b8-8841-4d85-826b-8a94277daecb)-Block.|In einer Methode, einem Indexer, einem Eigenschaftenaccessor oder einem Ereignisaccessor.|  
|try|Erstellt einen [try-catch](http://msdn.microsoft.com/library/cb5503c7-bfa1-4610-8fc2-ddcd2e84c438)-Block.|In einer Methode, einem Indexer, einem Eigenschaftenaccessor oder einem Ereignisaccessor.|  
|tryf|Erstellt einen [try-finally](http://msdn.microsoft.com/library/c27623fb-7261-4464-862c-7a369d3c8f0a)-Block.|In einer Methode, einem Indexer, einem Eigenschaftenaccessor oder einem Ereignisaccessor.|  
|unchecked|Erstellt einen [unchecked](http://msdn.microsoft.com/library/0c021f7c-923f-4b3d-a58f-55336f5ac27e)-Block.|In einer Methode, einem Indexer, einem Eigenschaftenaccessor oder einem Ereignisaccessor.|  
|unsafe|Erstellt einen [unsafe](http://msdn.microsoft.com/library/7e818009-1c6e-4b9e-b769-3728a01586a0)-Block.|In einer Methode, einem Indexer, einem Eigenschaftenaccessor oder einem Ereignisaccessor.|  
|Verwenden|Erstellt eine [using](http://msdn.microsoft.com/library/b42b8e61-5e7e-439c-bb71-370094b44ae8)-Direktive.|In einem Namespace (einschließlich des globalen Namespaces).|  
|while|Erstellt eine [while](http://msdn.microsoft.com/library/72a0765c-6852-4aca-b327-4a11cb7f5c59)-Schleife.|In einer Methode, einem Indexer, einem Eigenschaftenaccessor oder einem Ereignisaccessor.|  
  
## <a name="see-also"></a>Siehe auch  
 [Codeausschnittfunktionen](../ide/code-snippet-functions.md)   
 [Codeausschnitte](../ide/code-snippets.md)   
 [Vorgehensweise: Erstellen eines neuen Codeausschnitts mit Ersetzungen](http://msdn.microsoft.com/8d56d43c-097a-475b-aa85-cae1554b6338)   
 [Vorlagenparameter](../ide/template-parameters.md)   
 [Vorgehensweise: Verwenden von umschließenden Codeausschnitten](../ide/how-to-use-surround-with-code-snippets.md)   
 [Vorgehensweise: Wiederherstellen C# Refactoringausschnitten](../ide/how-to-restore-csharp-refactoring-snippets.md)
