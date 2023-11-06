````mermaid
classDiagram
    LottoControl: +run()
    LottoControl: -LottoIssuancePrograss()
    LottoControl: -LottoWinningPrograss()
    LottoControl --> LottoIssuance
    LottoIssuance --> PrintScreen
    PrintScreen --> LottosNumber
    PrintScreen --> Text
    PrintScreen --> LottoBuy
    LottoIssuance --> LottoBuy
    LottoIssuance --> LottoGenerator
    LottoIssuance --> LottosNumber
    LottoIssuance --> Request
    Request --> LottoBuy
    Request --> WinningLotto
    Request --> TextNumberConvert
    LottoControl --> PrintScreen
    LottoControl --> FindWinning
    FindWinning --> Request
    FindWinning --> LottoBuy
    FindWinning --> WinningLotto
    FindWinning --> PrintScreen
    FindWinning --> RateofReturn
    RateofReturn --> PrintScreen
    FindWinning --> enumWinning
    enumWinning-->NumberData
    enumWinning-->ErrorCheckWinning
    enumWinning-->Text
    ErrorCheck-->Text
    ErrorCheck-->WinningLotto
    ErrorCheck-->ErrorText
    ErrorCheck-->NumberData
    TextNumberConvert-->ErrorCheck
    interfaceViewr<--PrintScreen
    interfaceViewr<--enumWinning
    interfaceViewr<--Request
    interfaceinput<--Request

class LottoIssuance{
+void Issuance()
-List<Lotto> LottosGenerator(long)
}

class PrintScreen{
+void PrintLottoIssuanceNumber()
+void PrintLottoIssuance()
+void StartPrintWinningStatistics()
+void ShowRateofReturn()
}

class Request{
-long MoneyInputConversion(String)
-void MoneyInputMultipleRead()
+void RequestBuyMoney()
-Lotto WinningNumberInputConversion(String)
-void WinningNumberMultipleRead()
-void RequestLottoWinningNumber()
-int BonusNumberInputConversion(String)
-void BonusNumberMultipleRead()
-void RequestLottoBonusNumber()
+void RequestSetNumber()
}

class ErrorText{
+String errors
}
class Text{
+String usetext
}
class NumberData{
+int fixeddata
+long fixeddata
}

class ErrorCheck{
-long IsNumber64bit(String)
-void MoneyRange(long)
-void UnitConfirmation(long)
+long MoneyInput(String)
-int IsNumber(String)
-int WiningNumberRange(int)
-Lotto IsNumberMulti(List<String>)
-Lotto SeparatorWinnerNumber(String)
+Lotto WinnerNumberInput(String)
-int BonusNumberRange(int)
-void BonusDuplicateNumber(int, int)
-int CheckDuplicateNumber(String)
+int BonusNumberInput(String)
+void WinningValueOf()

}

class LottoGenerator{
+List<Integer> LottoNumberGenerator()
-List<Integer> NumberAscendingSort()
-List<Integer> RandomNumberGenerator()
}

class RateofReturn{
+void CalculateRateOfReturn(long, long)
}

class TextNumberConvert{
+long MoneyConvert(String)
+Lotto WinnerNumberConvert(String)
+int BonusNumberConversion(String)
}

class enumWinning{
-String textmatch
-int matchwinningcountnumber
-long prize
+void PrintWinnging(int)
-boolean matchCount(int)
+long GetWinningPrize()
+Winning valueOf(int, boolean)
}

class FindWinning{
-Winning Match(Lotto)
-Map<Winning, Integer> SetResult()
-Map<Winning, Integer> WinningCalculate(List<Lotto>, FindWinning)
-void PrintWinningStatistics(Map<Winning, Integer>)
-void WinningPriceTotal(Map<Winning, Integer>)
+void Result(List<Lotto>, FindWinning)
+void FindLottoWinning(List<Lotto> , FindWinning)
}

class LottoBuy{
-long buymoney
-long lottoIssuanceNumber
+void SetBuyMoney(long)
+void SetlottoIssuanceNumber(long)
+long GetBuyMoney()
+long GetLottoIssuanceNumber()
}

class LottosNumber{
-List<Lotto> lottos
+void SetLottos(List<Lotto>)
+List<Lotto> Lottos GetLottos()
}

class WinningLotto{
-Lotto winningnumber
-int bonusnumber
-long totalwinningprice
+void setWinningnumber(Lotto)
+void setBonusnumber(int)
+void setTotalWinningPrice(long)
+Lotto GetWinningNumber()
+int GetBonusNumber()
+long GetTotalWinningPrice()
}


class interfaceViewr{
+ViewPrint()
}
interfaceViewr<|.. UserScreen
class UserScreen{
+ViewPrint()
}

class interfaceinput{
+String GetData()
+void close()
}
interfaceinput<|.. Keyboard
class Keyboard{
+String GetData()
+void close()
}
````