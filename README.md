# Learning-about-stacks
leetcode的知识


void flatten(struct TreeNode* root)
{
    while(root)
    {
        if(root->left)
        {
            struct TreeNode * p = root->left;
            while(p->right) 
                p=p->right;

            p->right=root->right;
            root->right=root->left;
            root->left=NULL;
        }
        root=root->right;
    }
}
