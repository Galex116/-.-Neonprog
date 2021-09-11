# Импортирование модулей:
import telebot

# Авторизация Telegram:
bot = telebot.TeleBot(token="1993555174:AAE_3De2ZileT-Fzz8C8qHmr7UAFRqiALPY")

# Основная часть кода:
@bot.message_handler(commands=['start'])
def welcome(message):

    welcome_keyboard = telebot.types.ReplyKeyboardMarkup(True)
    welcome_keyboard.row("Что такое Neonprog?", "Почему именно мы?")
    welcome_keyboard.row("Что мы умеем?", "Наши контакты")
    welcome_keyboard.row("Как сделать заказ?", "Наши цены")

    bot.send_message(message.chat.id, "👋 Приветствую вас. Этот бот создан, чтобы вы поняли всю суть проекта Neonprog.\n"
                                      "\n"
                                      "👉 Выберите вопрос, который вас интересует: ", reply_markup=welcome_keyboard)

@bot.message_handler(content_types=['text'])
def send_text(message):

    welcome_keyboard = telebot.types.ReplyKeyboardMarkup(True)
    welcome_keyboard.row("Что такое Neonprog?", "Почему именно мы?")
    welcome_keyboard.row("Что мы умеем?", "Наши контакты")
    welcome_keyboard.row("Как сделать заказ?", "Наши цены")

    if message.text.lower() == "что такое neonprog?":
        bot.send_message(message.chat.id, "👨‍💻 Neonprog – Это платформа, предоставляющая IT услуги.\n"
                                          "Начинающий и быстро развивающийся проект, который помогает облегчить вашу работу.", reply_markup=welcome_keyboard)
    elif message.text.lower() == 'почему именно мы?':
        bot.send_message(message.chat.id, "1⃣ Цены. Делаем коды за их реальную стоимость\n\n"
                                          "2⃣ Индивидуальность. Найдем нужное решение задачи для каждого\n\n"
                                          "3️⃣ Мы продаем не услуги, а удобство. (Наши коды облегчат любую вашу работу)", reply_markup=welcome_keyboard)
    elif message.text.lower() == "что мы умеем?":
        bot.send_message(message.chat.id, "😉 Опишите задачу и я уверен, что мы найдем решение. На данный момент нельзя измерить точно, что мы сможем, а что нет. "
                                          "Можно только перечислить с чем уже работали:\n\n"
                                          "• Различные боты для вк и Telegram.\n"
                                          "• Доработки кодов.\n\n"
                                          "Список будет пополняться с каждым выполненным заказом…", reply_markup=welcome_keyboard)

    elif message.text.lower() == "наши контакты":
        bot.send_message(message.chat.id, "Наши контакты:\n"
                                          "\n"
                                          "Telegram:\n"
                                          "Наша группа - t.me/neonprog\n"
                                          "Администратор - @Alexander_Garushev\n"
                                          "\n"
                                          "ВКонтакте:\n"
                                          "vk.com/prosto_gorox\n"
                                          "\n"
                                          "❗ Администратор отвечает по любым вопросам.", reply_markup=welcome_keyboard)
    elif message.text.lower() == "как сделать заказ?":
        bot.send_message(message.chat.id, "❗ Чтобы сделать заказ, обратитесь к администратору:\n"
                                          "\n"
                                          "Telegram: @Alexander_Garushev\n"
                                          "ВКонтакте: vk.com/prosto_gorox", reply_markup=welcome_keyboard)
    elif message.text.lower() == "наши цены":
        bot.send_message(message.chat.id, "❕ Цену назначаете вы сами, мы обдумываем, стоит ли тот или иной код названной стоимости. Всегда можно договориться.")

bot.polling()

