package com.mrxamelax.volleybuddy;

import discord4j.core.DiscordClient;
import discord4j.core.GatewayDiscordClient;
import discord4j.core.event.domain.lifecycle.ReadyEvent;
import discord4j.core.event.domain.message.MessageCreateEvent;
import discord4j.core.object.entity.Message;
import discord4j.core.object.entity.User;
import reactor.core.publisher.Mono;

public class Volleybuddy {

    public static void main(String[] args) {
        DiscordClient client = DiscordClient.create("MTMyNDg2MDgyNTkxMDkwMjkyNg.G2DfGG.9LiAg4uzCIuWK2ZpjDPWn0cdjp7vOL-z09T7ko");

        Mono<Void> login = client.withGateway((GatewayDiscordClient gateway) ->
                gateway.on(MessageCreateEvent.class, event -> {
                    Message message = event.getMessage();

                    if (message.getContent().equalsIgnoreCase("!ping")) {
                        return message.getChannel()
                                .flatMap(channel -> channel.createMessage("pong!"));
                    }



                    return Mono.empty();
                })
        );

        login.block();

    }

}
