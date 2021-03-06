
## Dialog Management는 무엇인가? 
##### https://tutorials.botsfloor.com/dialog-management-799c20a39aad 공부

> ##### Intents - 의지, 의향이라는 사전적 의미를 가졌고 입력되는 글들이 어떠한 방향으로 해석이 되었으면 하는지에 대해서 알려주는 부분
> ##### Entity - 한건의 자료를 구성하는 레코드 하나

##### 챗봇을 만든다고 했을 때 사용자의 입력을 이해한 후 봇은 올바른 응답을 선택해야 한다. 이 응답은 사용자의 입력과 챗봇의 지식을 기반으로 하는데 이를 관리하는 것을 Dialogue Management라고 한다. 상용 AI 제품인 wit.ai, Dialogflow, LUIS와 같은 NLU 도구는 몇가지 기본적인 지원을 하지만 자체적인 결함이 있으므로 dialog management를 하기 위한 몇가지 방법을 알아보자

##### dialogue mangement의 주요한 기능은 사용자가 무엇을 말했을 때 대답을 찾는 것이다. 이 대답은 질문에 대한 대답이 될 수도 있고 더 많은 정보를 얻기 위한 질문일 수도 있다. 하지만 이보다 더 깊은 것이 이면에 있다. 챗봇의 원리 및 개념과 당면할 수 있는 몇가지 문제점에 대해 알아보자.

### Grounding
> ##### Grounding은 사용자에게 사용자가 무엇을 이야기 했는지를 알아들었다는 것을 알려준다. 이 Grounding을 통해 챗봇이 잘못된 정보를 말했을 경우 사용자는 이를 고쳐줄 수 있다.

### Slot filling
> ##### 사용자가 무엇을 물었을 때 챗봇은 질문 자체의 정보의 부족으로 인해 무엇을 찾아야 할지 모를 때가 있다. 해결방법은 사용자에게 더 많은 정보를 요구하는 것이다. 사용자의 intent(의도)를 바로 파악하는 대신에 dialogue management는 특정한 entities(자료)가 더 있어야 함을 깨닫는다. 만약 그렇지 않다면 필요한 정보를 다 얻을 때까지 사용자에게 entities를 요구할 필요가 있다. 이 원리를 slot filling이라고 한다. 

### Converation context
> ##### 사용자와 채팅을 할 때 모든 정보를 다 모아야 한다. 이를 conversation context라고 한다.

### Initiative (자주성, 주도성)
> ##### 대화를 할 때 한 사람이 대화를 주도하면 그 사람은 initiative를 가지고 있다고 한다. intent에 따라 사용자가 주도성을 갖고 싶다는 것을 나타낼 수가 있따. 그럼 챗봇은 그 대화에 맞춰나갈지 아니면 대화를 가져올 지 결정하게 된다. Mixed initiative의 좋은 예는 slot filling이다. 사용자가 어떤 것을 챗봇에게 물어봤을 때 챗봇은 더 많은 정보를 사용자에게 요구한다. 그러면 주도권은 사용자에게서 챗봇에게로 넘어가게 된다.

### Context switching
> ##### 사용자가 정해진 패턴대로 대화를 하면 좋겠지만 보통의 경우 그렇지 않다. 전의 대화가 끝나지 않은 채로 다음 대화가 이어지는 경우는 거의 없다. 이를 챗봇에게도 할 수 있도록 해야한다. 만약 사용자가 비행기를 예약하고 싶다고 하고 챗봇이 '어디로?'라고 물으면 사용자는 '나는 여행이 싫어, 레스토랑좀 찾아줘'라고 충분히 할 수 있다. 그럼 챗봇은 '레스토랑으로 가는 비행기를 찾을게'라고 하면 안된다. 이 예시에서 사용자는 첫번째 질문 이후에 새로운 주제의 질문을 함으로써 주도권을 찾아왔고 챗봇은 사용자가 '레스토랑을 찾아줘'라는 것이 주도권을 가져오는 intent라는 것을 알아차릴 수 있다. 이 때 챗봇은 전에 얘기했던 주제를 멈추고 새로운 주제에 대해 검색을 해야하는데 이를 context switching이라고 한다. 정리하면 context switching은 주제가 바뀌는 것을 얘기하는 것 같다. context siwtch가 되면 챗봇은 예전의 논의되었던 내용은 삭제 또는 나중을 위해 저장되어야 하고 새로운 주제에 신경써야 한다.

## Dialog management의 type
### Swtich statement
> ##### 가장 기본적인 dialog management의 type으로는 large switch statement가 있다. 모든 intent는 다른 대답을 야기한다. 이런 type의 dialog management는 사용자가 항상 주도권을 가진다. 따라서 이런 대화는 연결되어 있다는 느낌을 안준다. 이런 대화는 또한 Conversation context를 유지하지 못하고 챗봇이 무엇을 전에 얘기했는지를 기억하지 못한다.

### Finite state machine
> ##### 챗봇은 몇단계를 걸쳐 사용자가 정확한 답을 찾기를 바란다. 사용자가 어떤 얘기를 할때마다 챗봇은 사용자의 얘기를 바탕으로 대답을 찾아간다. 이런 방법을 Decision Diagram 또는 Finite State Machine이라고 한다. Finite State Machine의 힘은 상당히 광범위한데 대부분의 챗봇과의 대화는 FSM으로 이루어진다. 이는 사용자가 말한 것에 대한 정보가 제한적인 경우에 좋다. 왜냐면 계속 물을 수 있기 때문에... 하지만 이 방법도 결함이 있긴 하다. 가장 큰 결함은 이 방법은 유연하지가 못하다는 것이다. 두번째 단계를 거치지 않아도 되는 질문에 대해 두번째 단계를 거칠 수도 있다. 이는 챗봇이 받은 정보가 무엇을 의미하는지를 모를 경우에 발생할 수 있다.

### Goal based
> ##### 복잡한 대화에서는 대화를 상태의 세트로 생각할 수 있다. 그 이유는 상태는 상당히 빠르게 변하고 그렇게 되면 관리할 수가 없어지기 때문이다. 이를 다르게 생각하는 방법이 목표의 관점으로 생각하는 방법이다. 만약 사용자가 레스토랑을 찾아달라고 했으면 챗봇은 사용자의 의도 - 레스토랑을 찾아줘 -를 깨닫고 새로운 목표인 "레스토랑을 찾는다"를 설정한다. 챗봇은 이 목표를 달성하기 위해 레스토랑의 이름이 필요함을 사용자에게 알려준다. 만약 사용자가 레스토랑의 이름도 함께 말해줬다면 챗봇은 레스토랑의 이름을 물을 시간을 벌었다. 챗봇은 "레스토랑을 찾는다"라는 목표에 사용자의 질문이 적합한지를 확인하고 대답을 해준다. 이런 타입의 dialog management는 상태보다는 행동에 바탕을 둔다. 이는 챗봇이 사용자의 정보를 바탕으로 동일한 질문을 하거나 주제가 바뀌거나 (context switching) 의사결정을 할 때 더 쉽게 대처할 수 있도록 한다. 하지만 이는 setup이 어렵다.

### Belief based
> ##### NLU는 완벽하게 동작하지 않는다. 대부분의 NLU는 일정 정도의 불확실성으로 intent와 entity를 분류한다. 이는 NLU는 구체적인 규칙보다는 beliefs에 의해 추측됨을 의미한다. 시스템이 복잡해질수록 NLU는 잘못된 해석을 할 가능성이 높으며 Dialouge Management는 belief에 따라 동작되어야 한다.


## 위키 정리
##### (https://en.wikipedia.org/wiki/Dialog_manager)
##### DM으로의 input은 사람이 입력하고 이는 NLU 구성 요소에 의한 시스템 특정 의미 표현으로 반환된다. ##### DM은 state 변수를 가지고 있는데 그 변수에는 가령 대화 기록, 가장 최근에 대답하지 않은 질문 등등이 저장된다.
##### DM의 output은 dialog system의 다른 부분에 대한 명령 목록으로 일반적으로 의미론적인 표현으로 구성되어 있으며 이는 Natural language generation(NLG)에 의해 사람의 언어로 변환된다.

##### 다양한 DM이 있고 심지어 하나의 dialog system에 여러개의 DM이 있는 경우도 있다. 하지만 모든 DM에 공통적으로 적용되는 부분은 그것들이 상태 기반이라는 것이다. DM은 대략적으로 다음과 같이 구분이 된다.

##### 1. Input-control DM
##### 2. Output-control DM
##### 3. Strategic flow-control
##### - Hierarchical structure : 대화 모듈 스택 유지, 코드 재사용 가능, 백엔드에서 선택된 정보를 기반으로 즉각적으로 구축되는 동적 대화 작업을 허용
##### - Topic Tracking : 사용자가 주제를 정해주면 챗봇이 말하는 형태, 사용자는 OK, right 등의 수동적인 대답을 한다.
##### - Form Filling : 챗봇이 특정 정보를 요구하면 사용자가 그 특정정보를 다 얘기하는 형태, 가장 대표적인게 system-initiative인데 챗봇이 정보요구 - 사용자가 대답 이런 형태이다. slot의 order에 따라 사용자가 대답하지 않을 경우 챗봇은 이를 저장해두었다가 그것에 대해 더 묻지 않는다.
##### - Information state : 무엇인지 잘 모르겠다. input과 state에 따라 새로운 state를 적용할 수 있다는 내용인거 같은데...
##### - General Planning : 위의 Goal-based와 비슷한 내용인듯... 먼저 goal을 설정하게 하고 그 goal에 도달하기 위한 plan을 설정한 후 operation을 이룬다. 각 operation은 preconditions와 postconditions로 이루어져 있다. 
##### 4. Tactic flow-control - 몇몇 DM의 경우 대화의 구조와 목표 뒤에 전략적인 대화 결정을 내리는데 이는 대화의 질에 영향을 미친다.
##### - Error handling
##### - Initiative control
##### - Pedagogical decisions
##### - Learned tactics