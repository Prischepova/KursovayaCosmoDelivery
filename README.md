# `KursovayaCosmoDelivery`
![alt text](https://github.com/Prischepova/KursovayaCosmoDelivery/blob/Images/Logo.svg?raw=true)
***
`Prischepova Kseniia`
-----------
Мобильное приложение по доставке готовой еды – важный инструмент для ресторанов и подобных заведений, благодаря которому можно расширить возможности предприятия в сфере питания, вывести бизнес на новый уровень, увеличить прибыль, повысить конкурентоспособность заведения и лояльность клиентов. Сложность в реализации данной ИС заключается в том, что нужно учесть достаточно большое количество функций, процессов, элементов данных и сложные взаимосвязи между ними.
Ниже представлен код, с помощью которого получилось реализовать навигацию главного окна. Для того, чтобы все заработало, необходимо было поработать с терминалом. Надо было установить поды (Pod v1.11.3), модули, импортировать библиотеки. Также сложность заключалась в том, что не всегда совпадали версии и из-за этого навигация не работала.
Код реализации навигации в главном окне:
import React from 'react';
import {
   View,
   Text,
   Image,
   TouchableOpacity
} from 'react-native';
 
import {
   createDrawerNavigator,
   DrawerContentScrollView
} from "@react-navigation/drawer";
 
import { MainLayout } from "../screens";
import {
   COLORS,
   FONTS,
   SIZES,
   constants,
   icons,
   dummyData
} from "../constants";
 
const Drawer = createDrawerNavigator()
 
const CustomDrawerContent = ({navigation}) => {
   return (
       <DrawerContentScrollView
           scrollEnabled={true}
           contentContainerStyle={{ flex: 1 }}
       >
           <View
               style={{
                   flex: 1,
                   paddingHorizontal: SIZES.radius
               }}
           >
               {/* Close */}
               {/*<View
                   style={{
                       alignItems: 'flex-start',
                       justifyContent: 'center'
                   }}
               >
                   <TouchableOpacity
                       style={{
                           alignItems: 'start',
                           justifyContent: 'center'
                       }}
                       onPress={() => navigation.closeDrawer()}
                   >
                       <Image
                           source={icons.cross}
                           style={{
                               heght: 35,
                               width: 35,
                               tintColor: COLORS.white
                           }}
                       />
                   </TouchableOpacity>
                       </View>*/}
 
 
               {/* Profile */}
 
               {/* Drawer Items */}
           </View>
       </DrawerContentScrollView>
   )
}
 
const CustomDrawer = () => {
   return (
       <View
           style={{
               flex: 1,
               backgroundColor: COLORS.primary
           }}
       >
           <Drawer.Navigator
               drawerType="slide"
               overlayColor="transparent"
               drawerStyle={{
                   flex: 1,
                   width: '65%',
                   paddingRight: 20,
                   backgroundColor: 'transparent'
               }}
               sceneContainerStyle={{
                   backgroundColor: 'transparent'
               }}
               initialRouteName="MainLayout"
               drawerContent={props => {
                   return (
                       <CustomDrawerContent
                           navigation={props.navigation}
                       />
                   )
               }}
           >
               <Drawer.Screen name="MainLayout">
                   {props => <MainLayout {...props} />}
               </Drawer.Screen>
           </Drawer.Navigator>
       </View>
   )
}
 
export default CustomDrawer;
