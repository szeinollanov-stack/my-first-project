import java.util.*;

public class OnlinePsychologistBooking {

    static class Specialist {
        String name;
        String topic;

        public Specialist(String name, String topic) {
            this.name = name;
            this.topic = topic;
        }

        @Override
        public String toString() {
            return name + " (специализация: " + topic + ")";
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        List<String> topics = Arrays.asList("Стресс", "Мотивация", "Тревога", "Саморазвитие");

        List<Specialist> specialists = Arrays.asList(
                new Specialist("Иван Иванов", "Стресс"),
                new Specialist("Мария Петрова", "Мотивация"),
                new Specialist("Алексей Смирнов", "Тревога"),
                new Specialist("Елена Кузнецова", "Саморазвитие"),
                new Specialist("Ольга Сидорова", "Стресс"),
                new Specialist("Дмитрий Васильев", "Мотивация")
        );

        System.out.println("Выберите тему запроса:");
        for (int i = 0; i < topics.size(); i++) {
            System.out.println((i + 1) + ". " + topics.get(i));
        }

        int choice = 0;
        while (choice < 1 || choice > topics.size()) {
            System.out.print("Введите номер темы: ");
            if (scanner.hasNextInt()) {
                choice = scanner.nextInt();
                if (choice < 1 || choice > topics.size()) {
                    System.out.println("Неверный ввод. Попробуйте снова.");
                }
            } else {
                System.out.println("Пожалуйста, введите число.");
                scanner.next();
            }
        }

        String selectedTopic = topics.get(choice - 1);
        System.out.println("\nДоступные специалисты по теме \"" + selectedTopic + "\":");

        boolean found = false;
        for (Specialist s : specialists) {
            if (s.topic.equalsIgnoreCase(selectedTopic)) {
                System.out.println("- " + s);
                found = true;
            }
        }

        if (!found) {
            System.out.println("Специалисты по данной теме отсутствуют.");
        }

        System.out.println("\nСпасибо за использование сервиса записи к онлайн-психологу!");
    }
}
