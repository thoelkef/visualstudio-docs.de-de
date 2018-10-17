---
title: Debuggen einer T4-Textvorlage | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, troubleshooting
- text templates, debugging
ms.assetid: 0877fdf2-20bf-42da-b3cc-4c5856b80821
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: f299b89f7f59cbfc043bb77e6e56c3e5fac22d16
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49298908"
---
# <a name="debugging-a-t4-text-template"></a>Debuggen einer T4-Textvorlage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Haltepunkte in den Textvorlagen festlegen. Um eine Entwurfszeit-Textvorlage zu debuggen, speichern Sie die Textvorlagendatei, und wählen Sie dann **T4-Vorlage Debuggen** im Kontextmenü der Datei im Projektmappen-Explorer. Um eine Laufzeit-Textvorlage zu debuggen, müssen Sie einfach die Anwendung debuggen, zu der sie gehört.  
  
 Das Debuggen einer Textvorlage setzt das Verständnis der Schritte voraus, aus denen der Vorlagentransformationsprozess besteht. In jedem Schritt können andere Fehlerarten auftreten. Die Schritte werden im Folgenden beschrieben.  
  
|Schritt|Entwurfszeitvorlage: Vorkommen|Laufzeitvorlage: Vorkommen|  
|----------|--------------------------------------------|-----------------------------------------|  
|Code wird von der Textvorlage generiert.<br /><br /> Fehler in Direktiven bzw. falsch zugeordnete oder ungeordnete `<#…#>`-Tags.|Wenn Sie die Vorlage speichern oder Texttransformation aufrufen.|Wenn Sie die Vorlage speichern oder Texttransformation aufrufen.|  
|Generierter Code wird kompiliert.<br /><br /> Kompilierungsfehler im Vorlagencode.|Unmittelbar nach dem vorherigen Schritt.|Zusammen mit dem Anwendungscode.|  
|Code wird ausgeführt.<br /><br /> Laufzeitfehler im Vorlagencode.|Unmittelbar nach dem vorherigen Schritt.|Wenn die Anwendung ausgeführt wird und der Vorlagencode aufgerufen wird.|  
  
 In den meisten Fällen enthält der Fehlerbericht die Zeilennummern im Vorlagencode. Wenn der Fehlerbericht auf einen temporären Dateinamen verweist, ist dies in der Regel auf eine nicht übereinstimmende Klammer im Code der Textvorlage zurückzuführen.  
  
 Sie können Haltepunkte in den Textvorlagen festlegen und wie gewöhnlich debuggen.  
  
## <a name="common-errors-and-fixes"></a>Allgemeine Fehler und Korrekturmaßnahmen  
 In der folgenden Tabelle sind die gängigsten Fehler und ihre Behebung aufgeführt.  
  
|Fehlermeldung|Beschreibung|Lösung|  
|-------------------|-----------------|--------------|  
|Fehler beim Laden der Basisklasse „{0}“ , aus der die Transformationsklasse erbt.|Tritt auf, wenn Sie die Basisklasse nicht finden können, die im `inherits`-Parameter einer Vorlagenanweisung angegeben ist. Die Meldung gibt die Zeilennummer der Vorlagenanweisung an.|Stellen Sie sicher, dass die angegebene Klasse vorhanden ist und die zugehörige Assembly in einer Assemblyanweisung angegeben ist.|  
|Fehler beim Auflösen von include-Text für die Datei:{0}|Tritt auf, wenn Sie eine enthaltene Vorlage nicht finden können. Die Meldung enthält den Namen der angeforderten Includedatei.|Stellen Sie sicher, dass der Dateipfad relativ zum ursprünglichen Vorlagenpfad ist, oder dass sich die Datei an einem Speicherort befindet, der vom Host registriert ist, oder dass es einen vollständigen Pfad zur Datei gibt.|  
|Fehler beim Initialisieren des Transformationsobjekts. Die Transformation wird nicht ausgeführt.|Tritt auf, wenn die Initialize()-Funktion der Transformationsklasse gescheitert ist oder FALSE zurückgegeben wurde.|Der Code in der Initialize()-Funktion stammt aus der Basistransformationsklasse, angegeben der \<#@template#> die Richtlinie und von anweisungsprozessoren. Der Fehler, der verursacht hat, dass die Initialisierung gescheitert ist, ist auf der Fehlerliste aufgeführt. Überprüfen Sie, warum der Vorgang fehlgeschlagen ist. Sie können den tatsächlichen generierten Code für Initialize() betrachten, indem Sie die Schritte zum Debuggen einer Vorlage ausführen.|  
|Die Assembly "{0}'für den Direktivenprozessor"{1}' wurde nicht den FullTrust-Berechtigungssatz gewährt. Nur vertrauenswürdige Assemblys dürfen Anweisungsprozessoren bereitstellen. Dieser Anweisungsprozessor wird nicht geladen.|Tritt auf, wenn das System auf eine Assembly mit einem anweisungsprozessor keine FullTrust-Berechtigungen gewährt. Die Meldung enthält den Namen der Assembly und den Namen des Anweisungsprozessors.|Stellen Sie sicher, dass Sie nur vertrauenswürdige Assemblys auf dem lokalen Computer verwenden.|  
|Der Pfad "{0}" muss entweder lokal auf diesem Computer oder Teil Ihrer vertrauenswürdigen Zone sein.|Tritt auf, wenn eine Anweisung oder Assemblyanweisung auf eine Datei verweist, die nicht auf dem lokalen Computer oder in der vertrauenswürdigen Zone des Netzwerks ist.|Stellen Sie sicher, dass das Verzeichnis, in dem sich die Direktive oder Assemblydirektiven befinden, in der vertrauenswürdigen Zone ist. Sie können der vertrauenswürdigen Zone durch Internet Explorer ein Netzwerkverzeichnis hinzufügen.|  
|Mehrere Syntaxfehler z. B. "Ungültige Token-Erfassung" oder "Ein Namespace kann nicht direkt Member enthalten".|Zu viele schließende geschweifte Klammern im Vorlagencode. Der Compiler verwechselt dies mit dem Standardgenerierungscode.|Überprüfen Sie die Anzahl von schließenden geschweiften Klammern und Klammern in Codetrennzeichen.|  
|Schleifen oder Bedingungen nicht kompiliert oder korrekt ausgeführt. Beispiel: `<#if (i>10)#> Number is: <#= i #>`.<br /><br /> Dieser Code gibt immer den Wert i aus. Nur "Nummer ist:" ist bedingt.|Verwenden Sie in C# immer geschweifte Klammern, um Textblöcke zu umgeben, die in Steueranweisungen eingebettet sind.|Geschweifte Klammern hinzufügen: `<#if (i>10) { #>    Number is: <#= i #><# } #>`.|  
|„Ausdruck zu komplex“ beim Bearbeiten einer Entwurfszeitvorlage oder Kompilieren einer (vorverarbeiteten) Laufzeitvorlage.<br /><br /> [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] funktioniert nicht mehr, wenn Sie versuchen, von einer Laufzeitvorlage generierten Code zu überprüfen.|Textblock ist zu lang. T4 konvertiert Textblöcke in einen Zeichenfolgen-Verkettungsausdruck mit einem Zeichenfolgenliteral für jede Vorlagenzeile. Sehr lange Textblöcke können die Compiler-Größenbeschränkungen überschreiten.|Teilen Sie den langen Textblock mit einem Ausdrucksblock wie folgt:<br /><br /> `<#= "" #>`|  
  
## <a name="warning-descriptions-and-fixes"></a>Warnungsbeschreibungen und Korrekturen  
 In der folgenden Tabelle sind die gängigsten Warnungen zusammen mit Patches (sofern verfügbar) aufgeführt.  
  
|Warnmeldung|Beschreibung|Lösung|  
|---------------------|-----------------|--------------|  
|Beim Laden der Includedatei "{0}" null oder eine leere Zeichenfolge zurückgegeben.|Tritt auf, wenn eine enthaltene Textvorlagendatei leer ist. Der Meldung enthält den Dateinamen der enthaltenen Datei.|Entfernen Sie die Includeanweisung oder stellen sicher, dass die Datei Inhalt hat.|  
|Kompilieren von Transformation:|Stellt diese Zeichenfolge allen Fehlern oder Warnungen voran, die aus dem Compiler stammen, wenn die Transformation kompiliert wird. Diese Zeichenfolge bedeutet, dass der Compiler einen Fehler oder eine Warnung ausgelöst hat.|Wenn Sie ein Problem beim Suchen der DLL haben, müssen Sie möglicherweise entweder den vollständigen Pfad oder einen vollqualifizierten starken Namen angeben, wenn die DLL im GAC ist.|  
|Der Parameter „{0}“ ist bereits in der Anweisung vorhanden. Das Parameterduplikat wird ignoriert.|Tritt auf, wenn ein Parameter mehr als einmal in einer Anweisung angegeben wird. Die Meldung enthält den Namen des Parameters und die Zeilennummer der Direktive.|Entfernen Sie die doppelte Parameterspezifikation.|  
|Fehler beim Laden der Includedatei "{0}". Die Includeanweisung wird ignoriert.|Tritt auf, wenn Sie eine in einer `include`-Anweisung angegebene Datei nicht finden können. Die Meldung enthält den Namen der Datei und die Zeilennummer der Direktive.|Stellen Sie sicher, dass die Includedatei entweder im gleichen Verzeichnis wie die ursprüngliche Textvorlagendatei oder in einem der Includeverzeichnisse ist, die beim Host registriert sind.|  
|Eine ungültige Basisklasse wurde als Transformationsklasse angegeben. Die Basisklasse muss sich von Microsoft.VisualStudio.TextTemplating.TextTransformation ableiten.|Tritt auf, wenn der `inherits`-Parameter in einer Vorlagendirektive eine Klasse angibt, die nicht von `TextTransformation` erbt. Die Meldung gibt die Zeilennummer der Vorlagenanweisung an.|Geben Sie eine von der `TextTransformation`-Klasse abgeleitete Klasse an.|  
|Eine ungültige Kultur wurde in der template-Anweisung angegeben. Die Kultur muss das Format "xx-XX" aufweisen. Die invariante Kultur wird verwendet.|Tritt auf, wenn der Kulturparameter in einer Vorlagenanweisung falsch angegeben wird. Die Meldung gibt die Zeilennummer der Vorlagenanweisung an.|Ändern Sie den Kulturparameter in eine gültige Kultur im "xx-XX"-Format um.|  
|Ein ungültiger Debugwert "{0}" wurde in der template-Anweisung angegeben. Der Debugwert muss "True" oder "False" sein. Der Standardwert "False" wird verwendet.|Tritt auf, wenn der `debug`-Kulturparameter in einer Vorlagendirektive falsch angegeben wird. Die Meldung gibt die Zeilennummer der Vorlagenanweisung an.|Legen Sie den Debugparameter auf "True" oder "False" fest.|  
|Ein ungültiger HostSpecific-Wert „{0}“ wurde in der template-Anweisung angegeben. Der HostSpecific-Wert muss entweder "true" oder "false" sein. Der Standardwert "False" wird verwendet.|Tritt auf, wenn der hostspezifische Parameter in einer `template`-Direktive falsch angegeben wird. Die Meldung gibt die Zeilennummer der Vorlagendirektive an.|Legen Sie den hostspezifischen Parameter auf "True" oder "False" fest.|  
|Eine ungültige Sprache "{0}" wurde in der template-Anweisung angegeben. Die Sprache muss "C#" oder "VB" sein. Der Standardwert "C#" wird verwendet.|Tritt auf, wenn eine nicht unterstützte Sprache in der `template`-Direktive angegeben wird. Nur "C#" oder "VB" sind zugelassen (Groß-/Kleinschreibung wird nicht beachtet). Die Meldung gibt die Zeilennummer der Vorlagenanweisung an.|Legen Sie den `language`-Parameter in der Vorlagendirektive auf "C#" oder "VB" fest.|  
|Mehrere output-Direktiven wurden in der Vorlage gefunden. Alle außer der ersten werden ignoriert.|Tritt auf, wenn mehrere `output`-Anweisungen in einer Vorlagendatei angegeben werden. Die Meldung gibt die Zeilennummer der doppelten output-Direktive an.|Entfernen Sie doppelte `output`-Direktiven.|  
|Mehrere template-Direktiven wurden in der Vorlage gefunden. Alle außer der ersten werden ignoriert. Mehrere Parameter für die template-Direktive müssen innerhalb einer template-Direktive angegeben werden.|Tritt auf, wenn Sie mehrere `template`-Anweisungen innerhalb einer Textvorlagendatei (einschließlich enthaltener Dateien) angeben. Die Meldung gibt die Zeilennummer der doppelten template-Direktive an.|Aggregieren Sie die anderen `template`-Anweisungen in eine `template`-Anweisung.|  
|Für eine Anweisung mit dem Namen "{0}" wurde kein Prozessor angegeben. Die Anweisung wird ignoriert.|Tritt auf, wenn Sie eine `custom`-Direktive angeben, aber kein `processor`-Attribut bereitstellen. Die Meldung enthält den Namen der Anweisung und die Zeilennummer.|Stellen Sie ein `processor`-Attribut mit dem Namen des `directive`-Prozessors für die Anweisung bereit.|  
|Ein Prozessor mit dem Namen "{0}"konnte nicht gefunden werden für die Direktive mit dem Namen"{1}". Die Anweisung wird ignoriert.|Tritt auf, wenn das System den innerhalb einer `directive`-Direktive angegebenen `custom`-Prozessor nicht finden kann. Die Meldung enthält den Anweisungsnamen, den Prozessornamen und die Zeilennummer der Anweisung.|Legen Sie das `processor`-Attribut in der Anweisung auf den Namen des Anweisungsprozessors fest.|  
|Ein erforderlicher Parameter "{0}"für die Direktive"{1}' wurde nicht gefunden. Die Anweisung wird ignoriert.|Tritt auf, wenn das System keinen erforderlichen Direktivenparameter bereitstellt. Die Meldung enthält den Namen des fehlenden Parameters, den Anweisungsnamen und die Zeilennummer.|Stellen Sie den fehlenden Parameter bereit.|  
|Der Prozessor mit dem Namen "{0}"unterstützt nicht die Direktive mit dem Namen"{1}". Die Anweisung wird ignoriert.|Tritt auf, wenn ein Direktivenprozessor eine Direktive nicht unterstützt. Die Meldung stellt den Namen und die Zeilennummer der problematischen Direktive und den Namen des Direktivenprozessors bereit.|Korrigieren Sie den Namen der Anweisung.|  
|Die Includeanweisung für die Datei "{0}" verursacht eine Endlosschleife.|Wird angezeigt, wenn zirkuläre Includeanweisungen (Datei A enthält z. B. Datei B, die Datei A enthält) angegeben werden.|Geben Sie keine zirkulären Includedirektiven an.|  
|Ausführen von Transformation:|Stellt diese Zeichenfolge allen Fehlern oder Warnungen voran, die generiert werden, während die Transformation ausgeführt wird.|Nicht zutreffend.|  
|Ein unerwartetes Start- oder Endtag wurde in einem Block gefunden. Stellen Sie sicher, dass bei keinem Start- oder Endtag ein Schreibfehler vorliegt und dass keine geschachtelten Blöcke in der Vorlage vorhanden sind.|Angezeigt, wenn Sie eine unerwartete \<# oder #>. D. h. wenn man eine \<# nach einem anderen geöffneten Tag vorliegt, die nicht geschlossen wurde, oder Sie haben ein #>, wenn es kein geöffnetes Tag davor gibt. Die Meldung gibt die Zeilennummer des falsch zugewiesenen Tags an.|Entfernen Sie das nicht übereinstimmende Start- oder das Endtag, oder verwenden Sie ein Escape-Zeichen.|  
|Eine Anweisung wurde im falschen Format angegeben. Die Anweisung wird ignoriert. Geben Sie an der Richtlinie im format `<#@ name [parametername="parametervalue"]*  #>`|Vom Parser angezeigt, wenn eine Anweisung nicht im richtigen Format angegeben wird. Die Meldung gibt die Zeilennummer der falschen Anweisung an.|Werden Sie sicher, dass alle Anweisungen in der Form `<#@ name [parametername="parametervalue"]*  #>`. Weitere Informationen finden Sie unter [T4-Textvorlagenanweisungen](../modeling/t4-text-template-directives.md).|  
|Fehler beim Laden der Assembly "{0}'für den registrierten Direktivenprozessor"{1}"<br /><br /> {2}|Tritt auf, wenn ein Anweisungsprozessor nicht vom Host geladen werden konnte. Die Meldung identifiziert die für den Anweisungsprozessor und den Namen des Anweisungsprozessors bereitgestellte Assembly.|Stellen Sie sicher, dass der Anweisungsprozessor ordnungsgemäß registriert und die Assembly vorhanden ist.|  
|Fehler beim Suchen des Typs "{0}'in Assembly'{1}'für den registrierten Direktivenprozessor"{2}"<br /><br /> {3}|Tritt auf, wenn ein Anweisungsprozessortyp nicht von seiner Assembly geladen werden konnte. Die Meldung enthält den Namen des Typs, der Assembly und des Direktivenprozessors.|Der vshost sucht Direktivenprozessorinformationen (Name, Assembly und Typ) in der Registrierung. Stellen Sie sicher, dass der Anweisungsprozessor ordnungsgemäß registriert und der Typ in der Assembly vorhanden ist.|  
|Es wurde ein Problem beim Laden der Assemblys "{0}"|Tritt auf, wenn es ein Problem beim Laden einer Assembly gibt. Die Meldung stellt den Namen der Assembly bereit.|Sie können angeben, dass Assemblys, die zu ladenden in \<@# Assembly->-Anweisungen und von anweisungsprozessoren. Die Fehlermeldung, die dieser Zeichenfolge folgt, sollte weitere Daten darüber enthalten, warum die Assemblylast fehlgeschlagen ist.|  
|Es wurde ein Problem beim Erstellen und Initialisieren des Prozessors für eine Direktive mit dem Namen "{1}". Der Typ des Prozessors ist {0}. Die Anweisung wird ignoriert.|Tritt auf, wenn das System einen Direktivenprozessor nicht erstellen oder initialisieren konnte. Die Meldung stellt den Namen und die Zeilennummer der Anweisung und den Prozessortyp bereit.|Stellen Sie sicher, dass Sie den richtigen Anweisungsprozessor verwenden und dass der Anweisungsprozessor über einen öffentlichen Standardkonstruktor verfügt. Verwenden Sie andernfalls die Debugoptionen, um herauszufinden, warum die Initialize()-Methode des Anweisungsprozessors fehlschlägt. Weitere Informationen finden Sie unter [Textvorlagen Problembehandlung](../modeling/debugging-a-t4-text-template.md).|  
|Ausnahme beim Verarbeiten einer Anweisung mit dem Namen "{0}".|Tritt auf, wenn ein Anweisungsprozessor beim Verarbeiten einer Anweisung eine Ausnahme auslöst.|Stellen Sie sicher, dass die Parameter zum Anweisungsprozessor richtig sind.|  
|Der Host hat eine Ausnahme beim Versuch, den Assemblyverweis aufzulösen ausgelöst "{0}".|Tritt auf, wenn der Host eine Ausnahme auslöst, wenn er versucht, einen Assemblyverweis aufzulösen. Die Meldung stellt die Assemblyverweiszeichenfolge bereit.|Assembly kommen von \<@# Assembly #>-Anweisungen und von anweisungsprozessoren. Stellen Sie sicher, dass der Namenparameter im Assemblyparameter korrekt ist.|  
|Versucht, geben Sie nicht unterstützte {1} Wert '{0}"für Richtlinie {2}|Tritt durch den RequiresProvidesDirectiveProcessor (alle generierten Direktivenprozessoren leiten sich von ihm ab) auf, wenn Sie ein nicht unterstütztes anforderndes oder bereitstellendes Argument bereitstellen.|Stellen Sie sicher, dass die Namen der "Name='value'"-Paare korrekt sind.|



