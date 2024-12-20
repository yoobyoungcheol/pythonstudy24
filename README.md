# pythonstudy24
python AI 기초학습용

MBC아카데미 컴퓨터교육센터 수원점에서 AI기초학습으로 Python학습 진행용

https://wikidocs.net/book/1 학습용 책

```
# 미션
# 관리자가 커피 가격과 커피명을 정하고 개수를 입력합니다.
# 소비자가 커피를 구매하는데 진돈이 나와야 함
# 판매 종료 후 관리자가 커피 판매한 총금액을 파악할수 있어야함

prompt="""
1.  커피의 종류 와 가격 판매 개수 추가하기
2. 등록된 커피의 종류와 갯수 가격 확인하기
3. 커피의 등록 취소하기
4. 판매 시작하기
"""
money = 0
mymoney = 0
totalmoney = 0
customer = 0
addmin = 0
totalprice = []
i = 0
coffeeprice = {}
coffeesell ={}
coffeename = []
while True:
    while addmin != 5 :
        print(prompt)
        addmin = int(input("선택할 메뉴를 골라주세요 : "))
        match addmin:
            case 1:
                coffeename.append(str(input("추가할 커피를 입력하세요 : ")))
                coffeeprice[coffeename[i]] = {"가격":0}
                coffeesell[coffeename[i]] = {"수량":0}
                coffeeprice[name]["가격"] = int(input("가격을 입력해주세요 : "))
                coffeesell[name]["수량"] = int(input("수량을 입력해주세요 : "))
                i = i+1
            case 2 :
                u = 0
                if i == 0:
                    print("등록된 커피가 없습니다.")
                else:
                    for key in coffeename:
                        u = u+1
                        print("%d번 %s 가격: %d  수량 : %d   총가격 %d"%(u,key,coffeeprice[key]["가격"],coffeesell[key]["수량"],coffeeprice[key]["가격"]*coffeesell[key]["수량"]))
            case 3 :
                name = str(input("삭제할 커피의 이름을 입력하세요 : "))
                del coffeeprice[name]
                del coffeesell[name]
                i=i-1
            case 4 :
                break

    for key in coffeename:
        u = u+1
        print("%d번 %s 가격: %d  수량 : %d"%(u,key,coffeeprice[key]["가격"],coffeesell[key]["수량"]))
        totalprice.append(coffeeprice[key]["가격"])
        minprice = min(totalprice)
    while coffeesell:
        totalprice = []
        print("현재 잔액 %d원입니다."%totalmoney)
        money = int(input("돈을 투입하세요 : "))
        print("드실 커피를 선택하여 주세요")
        for key in coffeename:
            u = u+1
            print("%d번 %s 가격: %d  수량 : %d"%(u,key,coffeeprice[key]["가격"],coffeesell[key]["수량"]))
        customer = str(input("커피 이름을 골라주세요 : "))
        while money >= coffeeprice[customer]["가격"]:
            chice = int(input("상품의 수량을 선택해주세요 : "))
            if chice*money <= coffeeprice[customer]["가격"]*chice:
                print("잔액이 부족합니다.")
                break
            elif chice > coffeesell[customer]["수량"]:
                print("상품의 수량이 부족합니다.")
                break
            else:
                money = money - chice*coffeeprice[customer]["가격"]
                coffeesell[customer]["수량"] = coffeesell[customer]["수량"] - chice
                mymoney = mymoney+(chice*coffeeprice[customer]["가격"])
                totalmoney = totalmoney +money
            if coffeesell[customer]["수량"] == 0:
                del coffeesell[customer]
            print(coffeesell)
        print("돈이 부족합니다.")
    print("총매출 %d원입니다." %mymoney)

```
