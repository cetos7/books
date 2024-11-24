# Chapter 26 : The Main Component
--------------------

Trong mọi hệ thống, luôn có ít nhất một component tạo, điều phối và quan sát các component khác. Tôi gọi component này là `Main`.


## The Ultimate Detail
Component `Main` là chi tiết cuối cùng – chính sách cấp thấp nhất. Nó là điểm vào đầu tiên của hệ thống. Ngoài hệ điều hành thì không thứ gì phụ thuộc vào nó. Công việc của nó là tạo ra tất cả các Factory, Strategy, và các phương tiện toàn cục khác, và sau đó chuyển điều khiển cho các phần trừu tượng cấp cao của hệ thống.

Trong component `Main`, các phụ thuộc nên được chèn vào bởi một framework Dependency Injection (chèn phụ thuộc). Một khi chúng đã được chèn vào trong `Main`, `Main` sẽ phân phối những phụ thuộc này bình thường, mà không dùng framework.

Bạn hãy nghĩ `Main` như là component bẩn nhất trong tất cả các component bẩn.

Hãy xem component `Main` sau từ một phiên bản gần đây của Săn Tìm Wumpus. Lưu ý cách nó nạp tất cả các string mà chúng ta không muốn phần thân code của `main` biết.

```java
public class Main implements HtwMessageReceiver {
    private static HuntTheWumpus game;
    private static int hitPoints = 10;
    private static final List<String> caverns = new ArrayList();
    private static final String[] environments = new String[]{
        "bright",
        "humid",
        "dry",
        "creepy",
        "ugly",
        "foggy",
        "hot",
        "cold",
        "drafty",
        "dreadful"
    };


    private static final String[] shapes = new String[] {
        "round",
        "square",
        "oval",
        "irregular",
        "long",
        "craggy",
        "rough",
        "tall",
        "narrow"
    };

    private static final String[] cavernTypes = new String[] {
        "cavern",
        "room",
        "chamber",
        "catacomb",
        "crevasse",
        "cell",
        "tunnel",
        "passageway",
        "hall",
        "expanse"
    };
 
    private static final String[] adornments = new String[] {
        "smelling of sulfur",
        "with engravings on the walls",
        "with a bumpy floor",
        "",
        "littered with garbage",
        "spattered with guano",
        "with piles of Wumpus droppings",
        "with bones scattered around",
        "with a corpse on the floor",
        "that seems to vibrate",
        "that feels stuffy",
        "that fills you with dread"
    };
```

Đây là hàm `main`. Lưu ý cách nó dùng `HtwFactory` để tạo trò chơi. Nó truyền vào tên của lớp, `htw.game.HuntTheWumpusFacade`, bởi vì lớp đó thậm chí còn bẩn hơn `Main`. Điều này cản trở những thay đổi trong lớp đó khiến cho `Main` phải biên dịch lại/triển khai lại

```java
public static void main(String[] args) throws IOException {

    game = HtwFactory.makeGame("htw.game.HuntTheWumpusFacade", new Main());

    createMap();

    BufferedReader br = new BufferedReader(new InputStreamReader(System.in)); 
    game.makeRestCommand().execute();
    while (true) {

        System.out.println(game.getPlayerCavern());

        System.out.println("Health: " + hitPoints + " arrows: " +

        game.getQuiver());

        HuntTheWumpus.Command c = game.makeRestCommand();

        System.out.println(">");
        String command = br.readLine();

        if (command.equalsIgnoreCase("e"))

        c = game.makeMoveCommand(EAST);
        else if (command.equalsIgnoreCase("w"))

        c = game.makeMoveCommand(WEST);
        else if (command.equalsIgnoreCase("n"))

        c = game.makeMoveCommand(NORTH);

        else i (command.equalsIgnoreCase("s"))

        c = game.makeMoveCommand(SOUTH);

        else if (command.equalsIgnoreCase("r"))

        c = game.makeRestCommand();
        else if (command.equalsIgnoreCase("sw"))

        c = game.makeShootCommand(WEST);
        else if (command.equalsIgnoreCase("se"))

        c = game.makeShootCommand(EAST);
        else if (command.equalsIgnoreCase("sn"))

        c = game.makeShootCommand(NORTH);

        else if (command.equalsIgnoreCase("ss"))

        c = game.makeShootCommand(SOUTH);

        else if (command.equalsIgnoreCase("q"))

        return;

        c.execute(); 
    }
}
```
Cũng lưu ý rằng `main` tạo ra dòng đầu vào và bao gồm vòng lặp chính của trò chơi, biên dịch các lệnh đầu vào đơn giản, nhưng sau đó chuyển tất việc xử lý cho các component khác cấp cao hơn.

Cuối cùng, lưu ý rằng `main` tạo ra bản đồ:

```java
private static void createMap() {
    int nCaverns = (int) (Math.random() * 30.0 + 10.0);while (nCaverns-- > 0)
        caverns.add(makeName());

    for (String cavern : caverns) {
        maybeConnectCavern(cavern, NORTH);
        maybeConnectCavern(cavern, SOUTH);
        maybeConnectCavern(cavern, EAST);
        maybeConnectCavern(cavern, WEST);
    }

    String playerCavern = anyCavern();

    game.setPlayerCavern(playerCavern);

    game.setWumpusCavern(anyOther(playerCavern)); 
    game.addBatCavern(anyOther(playerCavern));
    game.addBatCavern(anyOther(playerCavern));
    game.addBatCavern(anyOther(playerCavern));
    game.addPitCavern(anyOther(playerCavern));
    game.addPitCavern(anyOther(playerCavern));
    game.addPitCavern(anyOther(playerCavern));

    game.setQuiver(5); 
}
// nhiều code đã loại bỏ...

}
```

Điều muốn nói ở đây đó là `Main` là một module cấp thấp bẩn trong vòng tròn ngoài cùng của kiến trúc tinh gọn. Nó nạp mọi thứ cho hệ thống cấp cao, và sau đó chuyển điều khiển cho nó.

## Conclusion
Hãy nghĩ `Main` giống như một plugin vào ứng dụng – một plugin thiết lập các điều kiện ban đầu và các cấu hình, tập hợp tất cả các tài nguyên bên ngoài, và sau đó chuyển điều khiển cho chính sách cấp cao của ứng dụng đó. Do nó là một plugin, nên có thể có nhiều `Main` component, mỗi một component `Main` cấu hình một kiểu cho ứng dụng của bạn.

Lấy ví dụ, bạn có thể có một plugin `Main` cho Dev, một cái khác cho Test, và một cái khác cho Production. Bạn cũng có thể có một plugin `Main` cho mỗi nước mà bạn phát hành ứng dụng tại đó, hoặc mỗi thẩm quyền, hoặc mỗi khách hàng.

Khi bạn nghĩ về `Main` như là một component plugin, phía sau một ranh giới kiến trúc, vấn đề về việc cấu hình sẽ trở nên dễ hơn rất nhiều để giải quyết.

