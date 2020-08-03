# Learning-about-stacks
leetcode的知识

一.Min Stack LCCI
How would you design a stack which, in addition to push and pop, has a function min which returns the minimum element? Push, pop and min should all operate in 0(1) time.

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/min-stack-lcci
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

①在栈的数据结构中添加一个数组存放最小值（每个区间的最小值，eg：0-1,0-2，0-3……）
②也可以建立新的堆栈——最小栈，专门存放最小值

#define MAX_SIZE 10000

typedef struct {
    int num[MAX_SIZE];
    int min[MAX_SIZE];
    int top;
} MinStack;

/** initialize your data structure here. */

MinStack* minStackCreate() {
    MinStack *obj = malloc(sizeof(MinStack));
    if(obj){
        obj->top = -1;
        return obj;
    }
    return NULL;
}

void minStackPush(MinStack* obj, int x) {
    obj->top++;
    obj->num[obj->top] = x;
    if(obj->top == 0)  
        obj->min[obj->top] = x;
    else 
        obj->min[obj->top] = fmin( obj->min[obj->top - 1], x);
}

void minStackPop(MinStack* obj) {
    if(obj->top<0) 
        return ;
    obj->top--;
}

int minStackTop(MinStack* obj) {
    return obj->top < 0 ? -1 : obj->num[obj->top];
}

int minStackGetMin(MinStack* obj) {
    return obj->top < 0 ? -1 : obj->min[obj->top];
}

void minStackFree(MinStack* obj) {
    free(obj);
}
