---
title: "CA2210: Assemblys m&#252;ssen g&#252;ltige starke Namen aufweisen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AssembliesShouldHaveValidStrongNames"
  - "CA2210"
helpviewer_keywords: 
  - "AssembliesShouldHaveValidStrongNames"
  - "CA2210"
ms.assetid: 8ed33d1c-8ec6-4b47-a692-e22dc8693088
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2210: Assemblys m&#252;ssen g&#252;ltige starke Namen aufweisen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AssembliesShouldHaveValidStrongNames|  
|CheckId|CA2210|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Eine Assembly ist nicht mit einem starken Namen signiert, der starke Name konnte nicht überprüft werden, oder der starke Name wäre ohne die aktuellen Registrierungseinstellungen des Computers ungültig.  
  
## Regelbeschreibung  
 Diese Regel ruft den starken Namen einer Assembly ab und überprüft ihn.  Ein Verstoß erfolgt, wenn einer der folgenden Punkte zutrifft:  
  
-   Die Assembly verfügt nicht über einen starken Namen.  
  
-   Die Assembly wurde nach der Signierung geändert.  
  
-   Die Signierung der Assembly erfolgt verzögert.  
  
-   Die Assembly wurde falsch signiert, oder die Signierung schlug fehl.  
  
-   Die Assembly muss Registrierungseinstellungen aufweisen, da sie sonst die Überprüfung nicht besteht.  Beispielsweise wurde das Strong Name\-Tool \(Sn.exe\) verwendet, um die Überprüfung der Assembly zu überspringen.  
  
 Der starke Name schützt Clients vor dem versehentlichen Laden einer manipulierten Assembly.  Assemblys ohne starke Namen sollten nur in ganz bestimmten Szenarien bereitgestellt werden.  Wenn Sie nicht einwandfrei signierte Assemblys freigeben oder verteilen, kann die Assembly manipuliert werden, die Common Language Runtime lädt die Assembly unter Umständen nicht, oder der Benutzer muss die Überprüfung auf dem Computer deaktivieren.  Eine Assembly ohne starken Namen weist die folgenden Nachteile auf:  
  
-   Ihr Ursprung kann nicht überprüft werden.  
  
-   Die Common Language Runtime kann die Benutzer nicht warnen, wenn der Inhalt der Assembly geändert wurde.  
  
-   Sie kann nicht in den globalen Assemblycache geladen werden.  
  
 Um eine verzögert signierte Assembly zu laden und zu analysieren, müssen Sie die Überprüfung der Assembly deaktivieren.  
  
## Behandeln von Verstößen  
 **So erstellen Sie eine Schlüsseldatei**  
  
 Verwenden Sie eines der folgenden Verfahren:  
  
-   Verwenden Sie das im [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-SDK enthaltene Assemblylinker\-Tool \(Al.exe\).  
  
-   Verwenden Sie bei [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], Version 1.0 oder Version 1.1, entweder das <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName>\-Attribut oder das <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>\-Attribut.  
  
-   Verwenden Sie bei [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] entweder die `/keyfile`\-Compileroption oder die `/keycontainer`\-Compileroption [\/KEYFILE \(Schlüsselcontainer oder Schlüsselpaar zum Signieren einer Assembly festlegen\)](/visual-cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly) bzw. die [\/KEYCONTAINER \(Schlüsselcontainer zum Signieren einer Assembly festlegen\)](/visual-cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly)\-Linkeroption in C\+\+\).  
  
 **So signieren Sie die Assembly in Visual Studio mit einem starken Namen**  
  
1.  Öffnen Sie die Lösung in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
2.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **Eigenschaften**.  
  
3.  Aktivieren Sie auf der Registerkarte **Signierung** das Kontrollkästchen **Assembly signieren**.  
  
4.  Wählen Sie unter **Schlüsseldatei mit starkem Namen auswählen** die Option **Neu** aus.  
  
     Das Fenster **Schlüssel für einen starken Namen erstellen** wird angezeigt.  
  
5.  Geben Sie unter **Schlüsseldateiname** einen Namen für den Schlüssel für einen starken Namen ein.  
  
6.  Wählen Sie aus, ob der Schlüssel mit einem Kennwort geschützt werden soll, und klicken Sie auf **OK**.  
  
7.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **Erstellen**.  
  
 **So signieren Sie die Assembly außerhalb von Visual Studio mit einem starken Namen**  
  
-   Verwenden Sie das Tool für starke Namen \(Sn.exe\), das vom [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-SDK bereitgestellt wird.  Weitere Informationen finden Sie unter [Sn.exe \(Strong Name Tool\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md).  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie nur dann eine Warnung dieser Regel, wenn die Assembly in einer Umgebung verwendet wird, in der die Manipulation ihres Inhalts unproblematisch ist.  
  
## Siehe auch  
 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName>   
 <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>   
 [Gewusst wie: Signieren einer Assembly mit einem starken Namen](../Topic/How%20to:%20Sign%20an%20Assembly%20with%20a%20Strong%20Name.md)   
 [Sn.exe \(Strong Name Tool\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md)