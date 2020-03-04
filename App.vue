<template>


    <view class="text-container">
        <status-bar
                background-color="blue"
                bar-style="light-content"
        />
        <scroll-view :content-container-style="{contentContainer: {
        paddingVertical: 20
    }}">
            <text>Hello World teste oioooodddosssoooi</text>


            <image
                    :style="{width: 50, height: 50}"
                    :source="{uri: 'https://facebook.github.io/react-native/docs/assets/favicon.png'}"
            />
            <image
                    :style="{width: 66, height: 58}"
                    :source="{uri: 'data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADMAAAAzCAYAAAA6oTAqAAAAEXRFWHRTb2Z0d2FyZQBwbmdjcnVzaEB1SfMAAABQSURBVGje7dSxCQBACARB+2/ab8BEeQNhFi6WSYzYLYudDQYGBgYGBgYGBgYGBgYGBgZmcvDqYGBgmhivGQYGBgYGBgYGBgYGBgYGBgbmQw+P/eMrC5UTVAAAAABJRU5ErkJggg=='}"
            />
            <text-input
                    :style="{height: 40, width: 100, borderColor: 'gray', borderWidth: 1}"
                    v-model="text"
            />
            <button
                    :on-press="onPressLearnMore"
                    title="Learn More"
                    color="#841584"
                    accessibility-label="Learn more about this purple button"
            />


        </scroll-view>

        <flat-list
                :data="[{key: 'a'}, {key: 'b'}, {key: 'e'}]"
                :render-item="(item) => renderList(item)"
        />
        <switch
                :on-value-change = "handleChange"
                :value = "value"/>
        <activity-indicator v-if="isLoading" size="large" color="#000fff"/>


    </view>

</template>

<style>
    .text-container {
        margin-top: 30px;
        alignItems: center;
    }
</style>
<script>
    import React from 'react';
    import {Text} from 'react-native';
    import { Alert } from 'react-native';

    export default {

        data: function () {
            return {
                text: '',
                isLoading:false,
                value: true

            };
        },

        methods: {
            onPressLearnMore: function () {
                Alert.alert(
                    'Alert Title',
                    'My Alert Msg',
                    [
                        {text: 'Ask me later', onPress: () => console.log('Ask me later pressed')},
                        {text: 'Cancel', onPress: () => console.log('Cancel Pressed'), style: 'cancel'},
                        {text: 'OK', onPress: () => console.log('OK Pressed')},
                    ],
                    { cancelable: false }
                );
                },
            renderList: function (item) {
                return (<Text>{item.item.key}</Text>)
            },
            handleChange: function(val) {
                this.value = val;
                if(val){
                    this.isLoading=true;
                }else {
                    this.isLoading=false;
                }
                console.log(val)
            }
        }
    }
</script>
